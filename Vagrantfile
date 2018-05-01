# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vm.hostname = 'perun'

  config.vm.box = 'stackhpc/centos-7'

  config.vm.provider 'virtualbox' do |vb|
    vb.memory = '4096'
    vb.linked_clone = true
  end

  config.vm.provider 'vmware_fusion' do |vmware|
    vmware.vmx['memsize'] = '4096'
    vmware.vmx['vhv.enable'] = 'TRUE'
    vmware.linked_clone = true
  end

  config.vm.provision 'shell', privileged: false, inline: <<-SHELL
    sudo yum -y install zsh tmux vim git python-virtualenv
    virtualenv ~/venvs/ansible
    source ~/venvs/ansible/bin/activate
    pip install -U pip
    pip install ansible
    SHELL
end
