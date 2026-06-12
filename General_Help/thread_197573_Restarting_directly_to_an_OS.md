---
title: "Restarting directly to an OS"
date: 2006-06-15
forum: General Help
---

### Post by seelk on 2006-06-15
I like the way Kubuntu gives you the ability to restart directly to a particular OS (ex. Windows).  Can this option be enabled in Ubuntu (Gnome)?

---

### Post by aysiu on 2006-06-15
Whoa! Kubuntu gives you that option? Care to share?

---

### Post by yager on 2006-06-15
Thats not fair!!! They get all the better tools and we get all the press!!!  I want my boot directly to Windows too.

---

### Post by reyfer on 2006-06-15
Maybe it's a stupid question, but I'm using Kubuntu 6.06 and i have not seen that feature, care to share?

---

### Post by seelk on 2006-06-16
In the log out window if you press and hold the Restart button you will get a choice to which OS to directly restart to.  I think it's a great feature since my default boot goes directly into Ubuntu which means I have to wait for Grub in order to select which OS.

---

### Post by aysiu on 2006-06-16
How did you discover that?

---

### Post by seelk on 2006-06-16
There's a drop-down arrow on the Restart button and I needed to find out what options this menu offered.

---

### Post by aysiu on 2006-06-16
Okay. I don't see it. I tried holding down the Restart button in the Kubuntu logout dialogue, and it did... nothing. How long do you have to hold it down for?

Does KDM have to be your default display manager?

I also didn't see a drop-down arrow...

---

### Post by seelk on 2006-06-16
Wait...  I think I'm confusing the distro I saw this in.  Before installing Ubuntu I tried other distros and I believe Suse/KDE gave that option.  My apologies I thought this option was enabled in Kubuntu.

I held the Restart button for a few seconds and the menu came up...

---

### Post by reyfer on 2006-06-16
It must be another distro, and another version of KDE, I can't find that feature in Kubuntu

---

### Post by scxtt on 2006-06-16
yeah, it's SUSE that does that ... i thought it was the coolest thing ever, too bad it didn't seem to work from remote x11 logins ... tho it probably would w/ a prog. like x11vnc ... you could always edit your menu.lst to default to whatever is installed on your machine - cept for that 1st time you boot into windows ... but you can get progs. in windows to edit ext* F/S ...

:-({|=

---

### Post by Gustav on 2006-06-16
I had thet to when I was running Mandrake (9-10) and it's a great feature.

I don't nned it anymore though since I never run my windows (it's still there because I've never had the energy to wipe the partition)

---

### Post by seelk on 2006-07-19
Has anyone found the way to accomplish this in Ubuntu??  Is that a Grub feature??

---

### Post by mbeierl on 2006-07-21
You could try rewriting the grub/menu.lst with the 

default 0

line set to the numerical position of the OS you want to boot next.

---

### Post by ewl1217 on 2006-07-21
This feature IS avaliable in Kubuntu. Somewhere in the KDE Control Center (can't remember exactly where, I'm not at my Kubuntu PC) there's an option to choose your boot manager. Just set it to Grub and you'll get the drop down menu. I'm not sure if this is something KDM-specific though. But someone could try seing if this works with GDM.

**EDIT:** I found [this thread]("http://ubuntuforums.org/showthread.php?t=200362"), which has more info on it. I think GNOME users may be out of luck though.

---

### Post by msak007 on 2006-07-22
Wish I saw (or searched for :)) that thread you linked to when I was looking for that info 2 weeks ago. I tried Arch Linux for a week and noticed that that option was there but wasn't in Kubuntu, so I started digging around in KDE's settings and found it under the Login Manager. I use KDE exclusively as well, so I can't really help when it comes to Gnome and how you can achieve the same there. It's a KDE feature, not a distro-specific feature (for once something that's not a SuSE specific tweak), so I wonder why that option is not set by default in Kubuntu. 

P.S. That feature is not only for booting into another OS - it reads your menu.lst file (in the case of grub) and grabs any other kernels you have installed too so you can boot directly into another kernel. So kind of like rebooting into "Safe Mode" in Windows from the shutdown menu, you can also choose to boot right into a recovery mode kernel if you're having problems.

---

