# ansible_recipes

## directory structure
see:
https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html#alternative-directory-layout

## Usage
Please, set private key files.
```
roles/store_secret_key/files/.ssh/development.pem
```

## command samples
```
# 疎通確認
ansible {inventory's role name} -m ping -i production/hosts -u {ssh user name} --private-key=~/.ssh/development.pem
# ex)
ansible ruby_on_rails_development -m ping -i production/hosts --private-key=~/.ssh/development.pem
# 以下のような感じで返却されればOK
hogehoge.com | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
```

```
# deploy
ansible-playbook -v ruby_on_rails_development.yml -i production/ --private-key=~/.ssh/development.pem
```

