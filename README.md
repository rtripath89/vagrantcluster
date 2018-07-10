Virtual HPC Cluster
===================

This repository contains the framework for a very basic HPC cluster based on Vagrant, Ansible, and OpenHPC.  It is just enough to build four nodes, a frontend, and a master node on your laptop or desktop system.  From there, you can customize it however you wish!

Getting Started
---------------

1. Install Vagrant: https://www.vagrantup.com/
1. Clone this repository
1. Run the `gensshkeys.sh` script to generate ssh keys in the ansible repository
1. Run `vagrant up` to fire up the cluster
1. Once the cluster is booted, you can run `vagrant ssh master` to log in to the master node, or `vagrant ssh fe1` to log in to the frontend
1. You can access your OpenonDemand by running 'localhost:4567' in your local browser.
1. Once all the VMs are up, log into fe1, using `vagrant ssh fe1`, and run `sudo scl enable httpd24 -- htpasswd -c /opt/rh/httpd24/root/etc/httpd/.htpasswd $USER` to add a user and password for you to access your OpenonDemand webapp.

A note on security
------------------
This virtual cluster is built around convenience, not security.  It uses Vagrant's default ssh keys for convenience, and it contains some private keys (for munge, for example).  This is good enough to run on an isolated desktop or laptop for experimentation, but you shouldn't plan to base an actual cluster configuration on its ansible repository without doing a good security sanity check.
