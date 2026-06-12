---
title: "Unable to login after dtc install"
date: 2010-09-01
forum: General Help
---

### Post by ahnilated on 2010-09-01
I had a mysql package that wouldn't install correctly and was informed that the fix was to install dtc.  Well I installed dtc and everything appeared to go fine.  I now can't log in as any user and the only way to get back onto the system is in repair mode.  Even uninstalling dtc with purge doesn't help.

What do I have to do to fix it so my logins work correctly again?  I have looked on Google and other sites for a fix and nothing seems to be working.  Any help would be greatly appreciated.

TIA

---

### Post by ahnilated on 2010-09-02
Anyone have any thoughts?  I am running Ubuntu 10.04 and have all the current updates.

---

### Post by kibrun on 2010-09-03
I'm facing the same problem. 

I did my DTC installation according to the DTC website ([http://dtcsupport.gplhost.com/PmWiki/DebianExpressSetup](http://dtcsupport.gplhost.com/PmWiki/DebianExpressSetup)). I picked debian since Ubuntu is based on debian distro. I added the "GPLHost Debian repository" into my /etc/apt/sources.list and continue on until end of installation following the documentation. All are fine and I can actually go into the DTC control panel(:D)

Problem started a few days after. I shutdown the server and left for about 2 weeks (having trouble with my ISP, save electricity by poweroff the machine since no connection anyway). So when my internet connection is on again, i logged into the server just to find that i got "authentication failure".. 

some reading brought me to this : [http://ubuntuforums.org/showthread.php?t=1323517](http://ubuntuforums.org/showthread.php?t=1323517)

I do recall of doing an update but can't remember the details.

now, I'm trying the installation again through VM. Will try to update later.

---

### Post by ahnilated on 2010-09-03
Thanks for the reply, keep me informed. :)

---

### Post by kibrun on 2010-09-17
i gave up installing DTC on ubuntu and follow the debian way 100% with Debian Lenny under VM. All is good and I can login into DTC, but the same thing happen (lock-out from system) after i purge the DTC and reboot. I don't know what happen. Fortunately this is VM so I just do reinstallation again. But for those who know/ might know, please do help to clarify thing or help to prevent this system lock-out. TQ.

---

### Post by ahnilated on 2010-09-17
Yeah, I installed Gentoo while I am waiting on another drive.  It is much faster and I don't have to worry about dtc.

---

