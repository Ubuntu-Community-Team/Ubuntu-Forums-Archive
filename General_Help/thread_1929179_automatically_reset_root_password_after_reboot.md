---
title: "automatically reset root password after reboot"
date: 2012-02-21
forum: General Help
---

### Post by bartmc on 2012-02-21
I need to synchronize the root password daily after a system reboot. It's a long story but suffice to say, the root password needs to change daily and the client is aware of what the password needs to be.  

My thoughts were to write a C Program to do it and give it sudo access. 

Anybody got anything better?  Ideally, a java program that launches after the reboot would do it but I'm flexible here.

---

### Post by roelforg on 2012-02-21
The /etc/passwd file contains all passwords, copying the hash from 1 machine to the other should work (refer to man passwd for more info)

---

### Post by lisati on 2012-02-21
Also see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by efflandt on 2012-02-21
The system is booted as root, so you could add something to or point to a script or binary from **/etc/rc.local** to do whatever you want to do.  So sudo is not necessary, but assume no environment and specify full paths to everything.

---

### Post by bartmc on 2012-02-21
The password is a complex algorithim based off the date. Nobody is ever going to guess it and it'd be quite hard to crack even knowing that it's based off the date. 

Here's the scenario. 

This is a thin client POS machine on an WAN. Joe Sales Clerk can't see anything but the POS software, it runs in "Full Screen Exclusive Mode". With a key combination and "today's password" a technician can drop to a terminal as the POS user, but he may need root access so I want to make sure the root password is the same as the "drop to a terminal" password. One of the issues we've had in the past on windows based PCs is that the admin password gets out and it's a free for all with the OS so we'd like to reset it daily and issue the password to the techs daily. We cannot depend on network connectivity so we have a complex but repeatable algorithim so that the passwords can be calculated for a disconnected computer. 

Think I'll just write a C program and have it run at startup.

---

