# -*- mode: ruby -*-
# vi: set ft=ruby :
box_name = "hashicorp/precise64"
static_ip = "192.168.111.8"

Vagrant.configure("2") do |config|

    config.vm.box = "#{box_name}"
    config.vm.network :forwarded_port, guest: 3000, host: 3000
    config.vm.network :forwarded_port, guest: 5432, host: 5432

    #might we need this for nfs?
    config.vm.network :private_network, ip: "#{static_ip}"

    config.vm.provision :ansible do |ansible|
      ansible.playbook = "provisioning/playbook.yml"
      ansible.extra_vars = {
        vagrant_static_ip: "#{static_ip}",
        ruby: "ruby-2.0.0",
        dbname: "hetexted_development",
        dbuser: "rails",
        dbpassword: "rails",
      }
    end
end
