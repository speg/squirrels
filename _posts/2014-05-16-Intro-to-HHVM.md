---
layout: "post"
---

# From Zero to Hack in Sixty Seconds

Want to try out Facebook\'s new language but don\'t know where to start?
I\'ve created a vagrant box to help you get started[fast](#fast).

<iframe width="420" height="315" src="//www.youtube.com/embed/w0K1wwSJZoc" frameborder="0" allowfullscreen="allowfullscreen">&nbsp;</iframe>

## Install VirtualBox

The box is designed for VirtualBox so head over to their[site](https://www.virtualbox.org)and grab the latest.

## Install Vagrant

In order to quickly configue a VM with a box we will be using[Vagrant](http://www.vagrantup.com). Once you have it install you will be able to use `vagrant` on the command line.

## Download the HHVM box

Vagrant uses \"boxes\" to build VirtualMachines. Think of them like simple disk images and may or may not already have some configuration done. I've made a box that has HHVM, nginx, and MariaDB already installed.

You can browse boxes on[VagrantCloud](http://vagrantcloud.com) and `vagrant` can fetch boxes from here. I have set up[this](https://vagrantcloud.com/speg/hhvm)box. To tell vagrant to download it, simply do: `vagrant box add speg/hhvm`

## Initialze the VM

Now that you\'ve got the box ready - it\'s time to set it up! Make a new directory and `cd` into it. Then run `vagrant init speg/hhvm`. vagrant will generate a Vagrant file. This is the configuration file for the VM. I like to uncomment the line in it that configures private networking. It should look like: `config.vm.network "private_network", ip: "192.168.33.10"`

There are a few different networking options, but this will at least give us a known IP address.

Now it's time to create the VM. Run `vagrant up` and sit back and watch the magic happen. A new VM will be created and configured based on the contents of the Vagrant file.

## Serving Content

Vagrant has automatically configured a shared folder with our VM. Our current folder is shared on the VM as `/vargrant` - which also happens to be the root directory for Nginx. So all we need to do is create an index file and we should be off and running.

`echo "<?hh echo 'Hello World';" > index.hh`

Now open up a browser to `192.168.33.10` (if you set up networking on that IP address) and you should see your first hack page!

## Database

There is also a MariaDB database installed. The user name and password are both `root` and the default database is named `hhvm`. it has a single table already set up (also called `hhvm`) with a couple rows of dummy data.


##<a name="fast">Quick Start</a>

* vagrant box add speg/hhvm
* vagrant init speg/hhvm
* vagrant up
* vim index.hh 




