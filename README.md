## Part 2
You should attempt to automate your work as much as possible, using ansible (and shell scripting). In places where you feel manual action is necessary, clear instructions (along with any scripts) should be provided to complete the exercise. 

1. Add the following to the Vagrantfile to provision a 3rd machine named `gitlab`, and provision it. 
```
  config.vm.define :gitlab, autostart: true do |gitlab|
    gitlab.vm.box = "centos/7"
    gitlab.vm.box_version = "2004.01"
    gitlab.vm.hostname = "gitlab.takehome.test"
    gitlab.vm.network "private_network", ip: "192.168.201.50"
    gitlab.vm.synced_folder ".", "/vagrant", disabled: true

    gitlab.vm.provider "virtualbox" do |virtualbox|
      virtualbox.customize [ "modifyvm", :id, "--cpus", "2" ]
      virtualbox.customize [ "modifyvm", :id, "--memory", "2048" ]
    end
  end
```
2. Setup gitlab community edition on this machine. Your setup should include the following
   - A way to pass in the root password during setup.
   - gitlab.takehome.test as the gitlab url
   - A gitlab runner on the same machine
   - Setup of https is not required
3. Create a test user, and a sample project with a simple gitlab pipeline to demonstrate the ability to run pipelines in this setup.
