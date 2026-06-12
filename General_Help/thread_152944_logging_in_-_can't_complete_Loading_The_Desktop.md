---
title: "logging in - can't complete Loading The Desktop"
date: 2006-03-30
forum: General Help
---

### Post by jmurda on 2006-03-30
while "Loading the Desktop" i get an error message saying kdesktop has crashed.

i have Yakuake installed so i can drop down a terminal to start kdesktop and kicker but it is annoying to have to do it every boot

anyone know an easy fix to this problem??


ty,
jmurda

---

### Post by sidd-tx on 2006-10-11
I kinda have the same problem. I too use yakuake, and I have it in startup. I made a link in the "/home/username/.kde/Autostart/" directory and it loads each time I login. 

This still works ok, but now on every login I get an error message from KDesktop:

"Error - KDesktop
file /home/username/.kde/Autostart/yakuake.desktop has no Type=... entry."

Yakuake still works, so this error message is more of annoyance than a crash problem. Anyone got a quick fix for this? 

Thanks in advance.
Sidd...

---

### Post by Colly on 2006-10-22
I think I'm having the same problem.
I installed Kubuntu-desktop Edgy EFT and when I login, I get a "kdesktop" error message window that opens and says:
"The process for the file protocol died unexpectedly"

---

### Post by Colly on 2006-10-30
> **Colly said:**
> I think I'm having the same problem.
I installed Kubuntu-desktop Edgy EFT and when I login, I get a "kdesktop" error message window that opens and says:
"The process for the file protocol died unexpectedly"

Nevermind.  I tried a complete uninstall (partition deleted) and fresh reinstall of the Kubuntu Edgy Desktop (6.10) and still get the same message.  Since I'm still new to this and haven't yet picked a favorite flavor of Ubuntu, I've decided to delete the partition and start over with Edubuntu Edgy 6.10.  I'll keep watching the forum to see if an answer appears.  I notice the same problem as mine appears to be posted in one of the French forums. Perhaps someone could post a translation here if an answer is already posted there.

---

### Post by Plautus on 2006-11-01
> **Colly said:**
> I think I'm having the same problem.
I installed Kubuntu-desktop Edgy EFT and when I login, I get a "kdesktop" error message window that opens and says:
"The process for the file protocol died unexpectedly"

I'm having this same problem with the same release of Kubuntu, I got the error on the first boot of the system and every subsequent boot. No idea at present what might be causing it.

---

### Post by fparri on 2006-11-04
Same problem, too, on a fresah install of edgy

---

### Post by ElijahLofgren on 2006-12-19
Some problem here on only 1 of my user accounts on Kubuntu Edgy (upgraded from Dapper). Still searching for the fix....

---

### Post by joneall on 2007-02-11
Same problem with Kubuntu Edgy on one old machine (not another). Details on Kubuntu Forum at

[http://kubuntuforums.net/forums/index.php?topic=11411.new#new](http://kubuntuforums.net/forums/index.php?topic=11411.new#new)

Help, please.

---

### Post by ElijahLofgren on 2007-02-11
I think this problem only happened when my machine was overloaded (I.E. multiple people logged in).

It could be that KDE needs more resources than that machine can provide. Maybe Xubuntu would be better for it.

---

### Post by Colly on 2007-02-13
I finally gave up on all the Edgy versions and went back to Dapper Drake Ubuntu (simplest one).
The PC I'm experimenting on only has 256mb RAM and a 300Mhz Celeron CPU.   Demanding too much of it is something I'm trying to avoid, so Ubuntu 6.06 LTS (Dapper Drake) seems the best choice and has so far proven to be the most stable.  Edgy couldn't even power down this PC completely.

In the post at the kubuntu forms, where the poster complains that qtparted doesn't do cylinders, I think they're going to find that with IDE drives, "doing cylinders" just isn't done.   Only MFM drives dealt with actual cylinders.  IDE drives remap everything inside them so that what's called a cylinder, isn't really anything but a logical construct being handled by the Intelligent Drive Electronics (which is where the term IDE comes from).  Even simple changes made to the BIOS setup in a PC can tell the IDE drive to handle "cylinders" differently.  Watch the cylinder count change when mode is switched from NORMAL to LBA and you can see that it's obvious that cylinders aren't something with which most users should attempt handling.   Pick a size for the partition and be glad that Linux doesn't make you deal with cylinders.

---

### Post by joneall on 2007-02-14
Thanks.  Yes, it seems to be a performance thing. Then why should a process break and why should one get all those messages in fdisk?  Sounds like a *bug* to me, definitely not a feature.

When does a problem slip over from being discussed on the forum to being submitted to the development folks to *fix?*

---

### Post by Colly on 2007-02-14
> **joneall said:**
> Thanks.  Yes, it seems to be a performance thing. Then why should a process break and why should one get all those messages in fdisk?  Sounds like a *bug* to me, definitely not a feature.

When does a problem slip over from being discussed on the forum to being submitted to the development folks to *fix?*

I guess when one of us gets bothered enough to go over to the bugs place and report it to the developers (instead of simply dropping back a version like I did - lazy me.)  :)  I think I looked at the bugs list and it was already reported and being worked on.   I expect something will eventually come out with repairs.  I'm not really paying close enough attention (haven't been checking) to know.

---

