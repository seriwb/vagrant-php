# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/xenial64"

  config.vm.hostname = "dev-php"

  if Vagrant::Util::Platform.windows?
    ENV["VAGRANT_DETECTED_OS"] = ENV["VAGRANT_DETECTED_OS"].to_s + " cygwin"
  end

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.network "private_network", ip: "192.168.33.11"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # If you are using Windows, it may be more faster and to use the RSync.
  # type: "rsync"
  config.vm.synced_folder "ansible", "/vagrant/ansible",
    :owner => 'vagrant', :group => 'vagrant',
    :mount_options => ['dmode=755', 'fmode=744']
  config.vm.synced_folder "repositories", "/vagrant/repositories",
    :create => 'true', :owner => 'vagrant', :group => 'vagrant',
    :mount_options => ['dmode=755', 'fmode=744']

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = "2"
  end

  config.vm.boot_timeout = 3600

  config.ssh.forward_agent = true

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL

#  config.vm.provision "ansible_local" do |ansible|
#    ansible.playbook = "/vagrant/ansible/php-developer.yml"
#    ansible.provisioning_path = "/vagrant/ansible"
#  end

end
