# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "centos-6.5", autostart: false do |config|
    config.vm.box = "chef/centos-6.5"
  end

  config.vm.define "debian-7.6", autostart: false do |config|
    config.vm.box = "chef/debian-7.6"
  end
  
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.customize ["modifyvm", :id, "--memory", "256"]
    vb.customize ["modifyvm", :id, "--cpus", 1]
    vb.customize ["modifyvm", :id, "--cpuexecutioncap", 100]
  end
  
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "test.yml"
    ansible.extra_vars = { ansible_ssh_user: "vagrant" }
  end

end
