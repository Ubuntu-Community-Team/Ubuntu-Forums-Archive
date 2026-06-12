---
title: "Problem accessing repos"
date: 2012-05-04
forum: General Help
---

### Post by MatthewPearce on 2012-05-04
Hello 

My netbook has been unable to find any of the Ubuntu Oneiric repos for a few weeks now. Example print out below.

1) I am connected to the internet.
2) I have also tried using connections elsewhere.
3) I have tried switching between the main repos and the UK repos using software sources. 

Can anyone suggest what the cause/solution might be.

a) Some setting on my netbook blocking access to the repos?
b) Having the wrong sources file?
c) Is there a sources.list I can download from somewhere in case mine got broken?

Thanks, I'm pretty stuck on this, and it's such a dumb problem :)

===============================================================
ERROR MESSAGE
===============================================================

user@userbook:~$ sudo apt-get install gnome-app-install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'software-center' instead of 'gnome-app-install'
The following packages will be upgraded:
  software-center
1 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
Need to get 697 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates/main software-center all 5.0.6
  Could not connect to 172.20.3.253:8080 (172.20.3.253), connection timed out
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.0.6_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.0.6_all.deb)  Could not connect to 172.20.3.253:8080 (172.20.3.253), connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

================================================================
MY /etc/apt/sources.list
================================================================

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse

###### Ubuntu Update Repos
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-proposed main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-proposed main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

---

### Post by plucky on 2012-05-04
> Could not connect to 172.20.3.253:8080 (172.20.3.253), connection timed out
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/..._5.0.6_all.deb](http://gb.archive.ubuntu.com/ubuntu/..._5.0.6_all.deb) Could not connect to 172.20.3.253:8080 (172.20.3.253), connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

You have a DNS problem as I cannot ping 172.20.3.253 as it gives a connection timeout.Are you using a proxy?

What happens if you put [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) into the address bar of your browser?

---

### Post by MatthewPearce on 2012-05-04
Hi Plucky

Using the browser [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) opens just fine.

I'm not using a proxy (that I know of) but am using wifi (same wifi as the last 8 months, but this problem only came up recently).

a) Would using a wire be likely to make any difference? [I'll give it a go]

b) Not sure what the relevant place to look for the problem proxy settings is?

I've uploaded a screenshot of (what I think are) my network proxy settings at:

[http://refute.me.uk/wp-content/uploads/2012/05/Screenshot-at-2012-05-04-121421.png]("http://refute.me.uk/wp-content/uploads/2012/05/Screenshot-at-2012-05-04-121421.png")

Much appreciated!

---

### Post by MatthewPearce on 2012-05-04
Update: using a wire makes no difference. Still get 

==============================


The following packages will be upgraded:
  software-center
1 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
Need to get 697 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates/main software-center all 5.0.6
  Could not connect to 172.20.3.253:8080 (172.20.3.253), connection timed out
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.0.6_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.0.6_all.deb)  Could not connect to 172.20.3.253:8080 (172.20.3.253), connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by plucky on 2012-05-04
What does ```
cat /etc/resolv.conf
``` show you?

---

### Post by MatthewPearce on 2012-05-04
Sorted :D

Solution
========

Expunged mentions of the proxy from

/etc/apt/apt.config            #think this one made the difference
/etc/wgetrc
/etc/environment


Plucky, thanks for the clue about proxy... didn't realise one could have sneaked in at some point.

---

