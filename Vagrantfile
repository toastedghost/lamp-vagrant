# -*- mode: ruby -*-
# vi: set ft=ruby :

VM_NAME="lamp"
VM_MEMORY=2048

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
    # ubuntu 14.04 lts 64 bit
    config.vm.box = "ubuntu/trusty64"

    # The url from where the 'config.vm.box' box will be fetched if it
    # doesn't already exist on the user's system.
    config.vm.box_url = "https://atlas.hashicorp.com/ubuntu/boxes/trusty64"

    # nicht auf Updates der Box checken
    config.vm.box_check_update = false

    # project environment
    config.vm.synced_folder "../", "/vagrant/dev"    
    
    # prepare the system for webserver duty
    config.vm.provision :shell, :path => "provision/bootstrap.sh"

    # name of server 
    config.vm.hostname = VM_NAME

    # network
    config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true

    # Virtualbox config, RAM, CPUs, etc.
    config.vm.provider "virtualbox" do |v|
        ### define VM name
        v.name = VM_NAME
        ### define size of ram
        v.memory = VM_MEMORY
        ### set maximum cpu usage
        v.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
        ### define number of cpus to use
        v.customize ["modifyvm", :id, "--cpus", "1"]
        ### active symbolic links under Windows
        v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
    end
end                                                                                                                                                               