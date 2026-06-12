---
title: "Yet another ssh no route to host"
date: 2010-08-26
forum: General Help
---

### Post by Dom11990 on 2010-08-26
I have googled this extensively over several days but none of the posts i found seemed to explain the solution very well. Obviously, I have a routing problem. The entire issue is resolved when I plug a lan cable into my laptop but I want to be able to ssh into my iphone with the wireless.

The setup I have is:
desktop running ubuntu 10
msi wind running ubuntu 9 that i upgraded to 10 using update manager
jailbroken iPhone 3.1.3 firmware with ssh installed

I can ssh from pc to the laptop and to the iphone.
I can also ssh from the laptop to the pc, no route to iphone.
The iPhone can ssh into the pc but times out when trying to ssh into the laptop. 

The weird thing is when I first installed all the ssh software everything worked perfectly. After a few ssh sessions the currently problem surfaced.

Does anyone have any idea how to fix this? Any help is greatly appreciated.

Dominik

---

### Post by blazemore on 2010-08-26
Can you ssh into the iPhone from any other system?

Can you "ping" the iPhone's IP address or hostname? What happens when you try?

---

### Post by Dom11990 on 2010-08-26
I am unable to ping the phone from the laptop
The response is "Destination Host Unreachable"
I don't have any other machines to test it on, but like i said, I can ssh into the phone without any problems from my desktop or when i plug the LAN cable into my laptop.

---

### Post by whiteychs on 2010-08-26
Well, I was getting this error in Arch Linux.

I had to allow all traffic from my local router in /etc/hosts.allow (on all computers) and then restart the daemon.

I'm not entirely sure how Ubuntu goes about this...

---

### Post by anirudhtomer on 2010-08-26
sometimes the destination host unreachable comes when the name resolution is not done.
so try to ping directly. I mean ping 192.x.x.x or whatever the IP is rather than pinging by its name like ping xyz.pqrs.com

---

### Post by Dom11990 on 2010-08-27
I have always used the IP addresses I found by right clicking my connection icon and going to "Connection Info" I'm sure they are right since I can ssh from my pc to both the laptop and the phone. So even with the correct IP ping it still says "Destination Host Unreachable".

---

### Post by Dom11990 on 2010-08-28
Help? Anyone? :(

---

### Post by meng1usa on 2010-09-11
> **Dom11990 said:**
> Help? Anyone? :(

this problem may rise because of that linux prefer the wired connection. if you use a wireless connection, disable the wired connection by following procedure:
1.find out the connection name by

ifconfig

2. disable it, eg. my wired connection name is eth0

sudo ifconfig eth0 down

then you should be able to build to ssh connection.

---

### Post by Plombo on 2010-09-14
I'm having a similar problem with SSH in Lucid: a "no route to host" error.  Pinging the server works fine with both the name and the IP address.  Trying to connect with SSH fails with both.

Another interesting note: I can connect and log in over SSH just fine from the same computer when I use PuTTY instead of command-line OpenSSH.

---

