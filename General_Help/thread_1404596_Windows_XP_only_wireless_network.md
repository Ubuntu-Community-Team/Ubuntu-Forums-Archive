---
title: "Windows XP only wireless network?"
date: 2010-02-11
forum: General Help
---

### Post by mullinsn2000 on 2010-02-11
I attend a community college that has 5 campuses.  All campuses have wireless networks.  For two weeks I have been trying to connect to their network with my netbook (Ubuntu 8.04) with no luck.  I call the IT department today and they tell me that their network ONLY supports Windows XP.  Windows 7, Vista, and all Linux OSes are unable to connect.  The network shows up but will not connect.  They do not know what the problem is or how to fix it.

Has anyone heard of something like this?

---

### Post by Jackzor on 2010-02-11
> **mullinsn2000 said:**
> I attend a community college that has 5 campuses.  All campuses have wireless networks.  For two weeks I have been trying to connect to their network with my netbook (Ubuntu 8.04) with no luck.  I call the IT department today and they tell me that their network ONLY supports Windows XP.  Windows 7, Vista, and all Linux OSes are unable to connect.  The network shows up but will not connect.  They do not know what the problem is or how to fix it.

Has anyone heard of something like this?

As far as I know it does not matter what the OS is. The router doesn't know. So I doubt it has anything to do with Ubuntu. I always seem to get fast internet speeds with ubuntu and I have never had any problems with beign unable to connect.

---

### Post by mullinsn2000 on 2010-02-11
> **Jackzor said:**
> As far as I know it does not matter what the OS is. The router doesn't know. So I doubt it has anything to do with Ubuntu. I always seem to get fast internet speeds with ubuntu and I have never had any problems with beign unable to connect.
This was my understanding also, but the person in the IT department said that only systems running XP could connect.  Possibly the software in the routers needs to be upgraded.  The worst part is when they said they do not know what the problem is so they cannot fix it.  I would be embarrassed to run an IT department of a college that offers degrees in IT but not be able to fix a network that only supports Windows XP.

---

### Post by Jackzor on 2010-02-11
Is there a login screen that you have to get past or are you simply not able to connect at all?

---

### Post by jflaker on 2010-02-11
Networks do not know about specific OS's.

The only thing I can think of is that they have a small applet that needs to run (which is a windows only app) that checks for open ports.  If the applet can not run, the network does not allow a connection.

Try running a 9.10 live CD...make sure you activate the restricted drivers to get your wireless card activated and see if it is because of an older release of Ubuntu....which had wireless networking troubles which were fixed in later releases.  If the LiveCD works, then that is the answer...you need to upgrade.

---

### Post by NFblaze on 2010-02-11
Soundslike you IT dude is just trying to find a convenient answer in order to pass the buck.

At my community college it was always a hassle to get on because we had so many users connected or trying to connect. What I can say is either come really early (or stay really late), before the bulk of the student body arrives and try to connect.

---

### Post by mullinsn2000 on 2010-02-11
> **jflaker said:**
> Networks do not know about specific OS's.
 
The only thing I can think of is that they have a small applet that needs to run (which is a windows only app) that checks for open ports. If the applet can not run, the network does not allow a connection.
 
Try running a 9.10 live CD...make sure you activate the restricted drivers to get your wireless card activated and see if it is because of an older release of Ubuntu....which had wireless networking troubles which were fixed in later releases. If the LiveCD works, then that is the answer...you need to upgrade.
 Windows 7 logs on fine.  Can I run 9.10 Live CD from a bootable USB drive?

---

### Post by jflaker on 2010-02-11
> **mullinsn2000 said:**
> Windows 7 logs on fine.  Can I run 9.10 Live CD from a bootable USB drive?

I believe you can. I've done it a few times....you may have to select an alternate boot as your machine boots...for dell, it is an F12

---

