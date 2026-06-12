---
title: "VirtualBox 3.0 on Ubuntu 8.04"
date: 2009-07-10
forum: General Help
---

### Post by mashcaster on 2009-07-10
Does anyone know how to install VirtualBox 3.0 on Ubuntu 8.04?  I downloaded and installed it but it does not seem to come up in the menu.  When I do:

sudo aptitude search VirtualBox-3.0

It displays a PI next to it instead of just a P or Just an I.

Anyone know what I have done wrong?

---

### Post by credobyte on 2009-07-10
Enable VirtualBox for your group ( System / Administration / Users and Groups ) & restart PC ( that's what I did on my 8.04 box a while ago ).

---

### Post by mashcaster on 2009-07-10
> **credobyte said:**
> Enable VirtualBox for your group ( System / Administration / Users and Groups ) & restart PC ( that's what I did on my 8.04 box a while ago ).

I'll try that when I get home.  Thanks.

---

### Post by mashcaster on 2009-07-10
I tried that and I was already a member.  So I tried reinstalling virtualbox and I got the following output:

> mashcaster@desktop:~$ sudo aptitude install virtualbox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  virtualbox-3.0 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/50.4MB of archives. After unpacking 107MB will be used.
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 108121 files and directories currently installed.)
Unpacking virtualbox-3.0 (from .../virtualbox-3.0_3.0.0-49315%5fUbuntu%5fhardy_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/virtualbox-3.0_3.0.0-49315%5fUbuntu%5fhardy_i386.deb (--unpack):
 trying to overwrite `/lib/modules/2.6.24-24-generic/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.24-24-generic
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-3.0_3.0.0-49315%5fUbuntu%5fhardy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
mashcaster@desktop:~$ 


---

