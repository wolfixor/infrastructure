🚀 Let's Run Your Playbooks:


Test connectivity first:
ansible repo-servers -i inventory/host.yaml -m ping


Run server preparation:
ansible-playbook -i inventory/host.yaml preparing.yaml --tags preparing_server


Install Docker:
ansible-playbook -i inventory/host.yaml preparing.yaml --tags docker_setup


Deploy repository server:
ansible-playbook -i inventory/host.yaml repo-server.yaml


🔍 Quick Analysis Commands:
Check what tasks will run:
ansible-playbook -i inventory/host.yaml preparing.yaml --list-tasks


Dry run:
ansible-playbook -i inventory/host.yaml preparing.yaml --check


Run specific tags:
ansible-playbook -i inventory/host.yaml preparing.yaml --tags "install_packages,hardening"

run traefik: 

ansible-playbook -i inventory/host.yaml preparing.yaml --tags traefik --limit development-server,staging-server,production-server



run think for limit server
ansible-playbook -i inventory/host.yaml preparing.yaml --tags preparing_server --limit development-server,staging-server,production-server


# Deploy to specific server gitlab
ansible-playbook -i inventory/host.yaml gitlab.yaml --limit iran-gitlab

# Or deploy to multiple servers gitlab
ansible-playbook -i inventory/host.yaml gitlab.yaml --limit development-server,staging-server

# gitlab runner
ansible-playbook -i inventory/host.yaml gitlab-runner.yaml --limit development-server



ansible-playbook -i inventory/host.yaml preparing.yaml --tags docker_setup --limit development-server,staging-server,production-server



ssh -i ~/.ssh/id_ed25519 -p 8945 root@188.121.122.150

ansible-vault decrypt inventory/group_vars/all/vault.yaml --ask-vault-pass

ansible-vault encrypt inventory/group_vars/all/vault.yaml

ansible-vault rekey inventory/group_vars/all/vault.yaml

ansible-vault view inventory/group_vars/all/vault.yaml

# Encrypt the vault file with new password
ansible-vault encrypt inventory/group_vars/all/vault.yaml

# Edit encrypted vault
ansible-vault edit inventory/group_vars/all/vault.yaml

ansible-playbook -i inventory/host.yaml preparing.yaml --tags proxy_setup
