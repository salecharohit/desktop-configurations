# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.network "public_network", ip: "192.168.0.16"
  config.vm.hostname = "devops"
  config.disksize.size = '40GB'

  config.vm.provider "virtualbox" do |vb|
    vb.name = 'devops'
    vb.memory = 4096
    vb.cpus = 2
	vb.gui = false

  end
  
  config.vm.provision "shell",privileged: true, inline: <<-SHELL
	apt-get update && apt-get upgrade
	apt-get install -y git
	apt-get install -y curl
	apt-get install -y wget
	apt-get install -y  apt-transport-https ca-certificates curl software-properties-common
	curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
	add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
	apt-get update
	apt-get install -y  docker-ce
	usermod -aG docker vagrant
	curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
	chmod +x /usr/local/bin/docker-compose
  SHELL

end