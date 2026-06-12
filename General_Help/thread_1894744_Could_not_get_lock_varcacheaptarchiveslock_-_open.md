---
title: "Could not get lock /var/cache/apt/archives/lock - open"
date: 2011-12-13
forum: General Help
---

### Post by Randymanme on 2011-12-13
On Ubunut 11.10, I attempted to use Muon Package Manager to install  Mint-Meta-Gnome-DVD.  Muon got stuck preparing sun-java-jre; after an  hour or so, I turned it off at the commandline. Now, when I attempt to  run Synaptic, I first get a notification of a broken package.  After  selecting the broken package filter, synaptic indicates that the unmet  dependency is resolved.  When I attempt to reinstall or remove the  partially installed Mint-Meta-Gnome-DVD, I get the following message: 

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable) 
E: Unable to lock the download directory.

And when I attempt to resolve the problem in the terminal, I get the following:

randyman@randyman-Dimension-8300:~$ sudo apt-get remove mint-meta-gnome-dvd 
[sudo] password for randyman: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
You might want to run 'apt-get -f install' to correct these: 
The following packages have unmet dependencies: 
 sun-java6-plugin : Depends: sun-java6-bin (>= 6.26-1maverick1) but it is not going to be installed 
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
randyman@randyman-Dimension-8300:~$ sudo apt-get -f install 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Correcting dependencies... Done 
The following packages were automatically installed and are no longer required: 
  apg geoclue-ubuntu-geoip gnome-online-accounts gnome-control-center-data 
Use 'apt-get autoremove' to remove them. 
The following extra packages will be installed: 
  sun-java6-bin sun-java6-jre 
Suggested packages: 
  sun-java6-fonts ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho 
  ttf-sazanami-mincho ttf-arphic-uming 
The following NEW packages will be installed: 
  sun-java6-bin sun-java6-jre 
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded. 
21 not fully installed or removed. 
E:
E: Unable to lock directory /var/cache/apt/archives/ 
randyman@randyman-Dimension-8300:~$ 

What should I do?  Any advice will be appreciated. 

Thanks.

---

### Post by Bucky Ball on 2011-12-13
> **Randymanme said:**
> 
You might want to run 'apt-get -f install' to correct these: 


... add sudo to the beginning of the command.

---

### Post by Randymanme on 2011-12-13
Thank you for the quick reply.


 Enrico "eNry" Carafa (mr.tennents) at 
[https://answers.launchpad.net/ubuntu/+question/181752](https://answers.launchpad.net/ubuntu/+question/181752)

referred me to  [http://askubuntu.com/questions/15433/fixing-could-not-get-lock-var-lib-dpkg-lock.  ]("http://askubuntu.com/questions/15433/fixing-could-not-get-lock-var-lib-dpkg-lock")

sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock

---

### Post by drmrgd on 2011-12-13
Anytime that I've seen that error after a crashed install the easiest way I found to fix it was to reboot.  It seems the dpkg installer gets hung up and can't work with the apt directory anymore.  I'm not sure if you tried it or not, but a simple reboot may fix this.  I'd love to know if there is an easier way, though.

---

### Post by drmrgd on 2011-12-13
> **Randymanme said:**
> Thank you for the quick reply.


 Enrico "eNry" Carafa (mr.tennents) at 
[https://answers.launchpad.net/ubuntu/+question/181752](https://answers.launchpad.net/ubuntu/+question/181752)

referred me to  [http://askubuntu.com/questions/15433/fixing-could-not-get-lock-var-lib-dpkg-lock.  ]("http://askubuntu.com/questions/15433/fixing-could-not-get-lock-var-lib-dpkg-lock")

sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock

Oh, cool!  There's the more simple solution I was looking for.  I'll have to try that next time.

---

