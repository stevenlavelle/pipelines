# Defines our Vagrant environment
#
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # create mgmt node
  config.vm.define :mgmt do |mgmt_config|
      mgmt_config.vm.box = "ubuntu/focal64"
      mgmt_config.vm.hostname = "mgmt"
      mgmt_config.vm.network "forwarded_port", guest: 80, host: 8085
      mgmt_config.vm.network :private_network, ip: "10.0.15.10"
      mgmt_config.vm.provider "virtualbox" do |vb|
        vb.memory = "4096"
      end
      mgmt_config.vm.provision :shell, path: "bootstrap-mgmt.sh"
  end

  # create worker node
  config.vm.define :worker do |worker_config|
      worker_config.vm.box = "ubuntu/focal64"
      worker_config.vm.hostname = "worker"
      worker_config.vm.network :private_network, ip: "10.0.15.11"
      worker_config.vm.network "forwarded_port", guest: 80, host: 8086
      worker_config.vm.provider "virtualbox" do |vb|
        vb.memory = "4096"
      end
  end
end
