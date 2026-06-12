---
title: "Installing Java messed my ubuntu up"
date: 2010-08-10
forum: General Help
---

### Post by JustLikeYouImagined on 2010-08-10
I had ubuntu 10.04 LTS installed on my laptop through wubi. I tried installing Java. I basically followed instructions from a ubuntu webpage. After I was done, I restarted and guess what! The internet doesn't work anymore. Both the network cards, wireless and wired, got disbaled somehow. 
I typed something like $lshw -C network, and it said both eth0 and eth1 were disabled. 
I tried editing the /etc/network/interfaces file but that didn't work either. So I finally uninstalled the wubi installation. I'm planning to re-install ubuntu, this time not through wubi. And I still need Java.
Can somebody please what I should and shouldn't do this time? Which Java is the most recommened for ubuntu and how do I install it?

Pls keep it simple, I'm a complete linux newbie.

Thanks.

---

### Post by krishnandu.sarkar on 2010-08-10
Installing Java is simple and it really doesn't mess with ubuntu. Search the forum and you'll get many proves. BTW I've no idea what you did and why all these happed.

You can install java by running this command in terminal:

sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

---

### Post by krishnandu.sarkar on 2010-08-10
Installing Java is simple and it really doesn't mess with ubuntu. Search the forum and you'll get many proves. BTW I've no idea what you did and why all these happed.

You can install java by running this command in terminal:

sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

---

