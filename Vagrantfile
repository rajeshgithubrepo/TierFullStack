Vagrant.configure("2") do |config|
  
  # Global configuration for all VMs
  config.vm.synced_folder "./scripts", "/home/vagrant/Host_shared"

  # Define the first VM: Web Server
    config.vm.define "master" do |master|
      master.vm.box = "ubuntu/jammy64"
      master.vm.network "private_network", ip: "192.168.50.4"
      master.vm.provider "virtualbox" do |vb|
        vb.memory = "3072"
        vb.cpus = 2
      end
      #master.vm.provision "shell", path: "scripts/setup_master.sh"

      # Forward port from the host to the VM
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 8080, host: 8080
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 3000, host: 3000
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 9090, host: 9090
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 9000, host: 9000
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 32630, host: 32630
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 22, host: 22
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 8081, host: 8082
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 6443, host: 6443
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 465, host: 465
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 80, host: 80
      master.vm.network "forwarded_port", host_ip: "127.0.0.4", guest: 9115, host: 9115
    end

  # Define the third VM: SonarQ Server
    config.vm.define "sonar" do |sonar|
      sonar.vm.box = "ubuntu/jammy64"
      sonar.vm.network "private_network", ip: "192.168.50.5"
      sonar.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        vb.cpus = 2
      end
      #sonar.vm.provision "shell", path: "scripts/setup_docker.sh"

      # Forward port 8080 from the host to the VM
      sonar.vm.network "forwarded_port", host_ip: "127.0.0.5", guest: 9000, host: 9000
    end
end
