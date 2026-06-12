---
title: "How Do I Install a Newer Version of a Package Than Exists in the Repo?"
date: 2010-08-13
forum: General Help
---

### Post by rhp997 on 2010-08-13
I am running Ubuntu 9.04 at work and have a sudden need to install a newer version of python-support (> 0.9.0) than is currently available in the repo (0.8.7) for my Ubuntu [version]("https://launchpad.net/ubuntu/+source/python-support").  Upgrading to 9.10 is not an option as we are planning to jump to 10.04 LTS in the next few months and I am unable (unwilling) to mess with a complete upgrade prior.  Is it possible for me to upgrade to the newest version of python-support - or is this package OS version specific?  Assuming it's possible, how might I go about the process of upgrading?

Although this question pertains specifically to the python-support package, might the answer also relate to other packages?  In general, is this practice frowned upon?

---

### Post by zvacet on 2010-08-13
Is [this]("https://launchpad.net/~deluge-team/+archive/ppa") what are you looking for?

---

### Post by rhp997 on 2010-08-13
@zvacet - Thanks for the link; I was able to get the latest version of python-support by using the following:

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo echo "deb [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) jaunty main" >>/etc/apt/sources.list 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
sudo apt-get update
sudo apt-get upgrade --assume-yes

---

