---
title: "SU Authentication Failure  in terminal...?"
date: 2011-05-29
forum: General Help
---

### Post by ZacharyD on 2011-05-29
Hey guys, i'm having a problem... su doesn't work in terminal. I searched the forum to make sure someone else hasn't had this problem, but found nothing. Well, i found [one (click)]("http://ubuntuforums.org/showthread.php?t=1763241"), and tried it, but it didn't fix it. Everything else works. Sudo, Software manager, synaptic package manager... I know i'm putting the right password in.  

Heres a picture, ignore everything except the last 4 lines.

[IMG]http://i55.tinypic.com/2weko5i.jpg[/IMG]



 Everything before it was me trying a proposed fix in the thread mentioned above. 
> 
sudo dpkg --configure -a 
sudo apt-get clean 
sudo apt-get update 
sudo apt-get upgradeI've tried changing my password as well. I got the same error. 
[IMG]http://i52.tinypic.com/348n04l.jpg[/IMG]

Also, "sudo su" works fine. I'm not sure if theres a difference as i'm new to ubuntu....linux in general. Can you explain the difference between sudo and su, and sudo su? Also, can you explain what any commands you need me to do are? that way, i'm not just leaching.


--- All i'm trying to do is install Java! XD 

Sysinfo:
> 
Release: Ubuntu 11.04 (natty)
GNOME: 2.32.1
Kernal: 2.6.38-8-generic



Thanks!

---

### Post by CharlesA on 2011-05-29
The root account is locked by default, so you can't use "su" to switch to root.

Use sudo to run a command with root privileges.

---

### Post by ZacharyD on 2011-05-29
> **CharlesA said:**
> The root account is locked by default, so you can't use "su" to switch to root.

Use sudo to run a command with root privileges.
So sudo works in place of su all the time?

---

### Post by WorMzy on 2011-05-29
Kinda. Only use "sudo" for terminal apps, and "gksu", "gksudo" or "kdesu" for graphical apps. Using sudo for graphical apps can cause problems with your home folder's permissions.

---

### Post by wildmanne39 on 2011-05-29
> **ZacharyD said:**
> Hey guys, i'm having a problem... su doesn't work in terminal. I searched the forum to make sure someone else hasn't had this problem, but found nothing. Well, i found [one (click)]("http://ubuntuforums.org/showthread.php?t=1763241"), and tried it, but it didn't fix it. Everything else works. Sudo, Software manager, synaptic package manager... I know i'm putting the right password in.  

Heres a picture, ignore everything except the last 4 lines.

[IMG]http://i55.tinypic.com/2weko5i.jpg[/IMG]



 Everything before it was me trying a proposed fix in the thread mentioned above. 
I've tried changing my password as well. I got the same error. 
[IMG]http://i52.tinypic.com/348n04l.jpg[/IMG]

Also, "sudo su" works fine. I'm not sure if theres a difference as i'm new to ubuntu....linux in general. Can you explain the difference between sudo and su, and sudo su? Also, can you explain what any commands you need me to do are? that way, i'm not just leaching.


--- All i'm trying to do is install Java! XD 

Sysinfo:



Thanks!
Hi, take a look at this it might help you understand sudo. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by CharlesA on 2011-05-29
> **WorMzy said:**
> Kinda. Only use "sudo" for terminal apps, and "gksu", "gksudo" or "kdesu" for graphical apps. Using sudo for graphical apps can cause problems with your home folder's permissions.

Indeed. sudo has problems with redirects, but there are ways around that.

> **wildmanne39 said:**
> Hi, take a look at this it might help you understand sudo. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Check out this link for more info.

---

