---
title: "Ubuntu won't boot"
date: 2009-10-20
forum: General Help
---

### Post by abiggs on 2009-10-20
Hi all,

Apologies for the simplicity I require. I'm running Jaunty, dual booting with Vista Ultimate. I have an ATI Radeon HD 2400 card. I've had no problems with Ubuntu except it occasionally not recognizing my external HD, which is what happened this morning. I restarted it in order to recognize the HD but after showing the Ubuntu text above the loading progress bar, the ubuntu text appeared in strange colours with several red dots at the top of the screen. It flashed white then returned to the strange Ubuntu text several times before the screen went blank. 

I'm really not great at all this, and my knowledge is terrible, but if anybody can see what's going on here, I'd greatly appreciate your help!

Cheers,

Biggs

---

### Post by oboedad55 on 2009-10-20
> **abiggs said:**
> Hi all,

Apologies for the simplicity I require. I'm running Jaunty, dual booting with Vista Ultimate. I have an ATI Radeon HD 2400 card. I've had no problems with Ubuntu except it occasionally not recognizing my external HD, which is what happened this morning. I restarted it in order to recognize the HD but after showing the Ubuntu text above the loading progress bar, the ubuntu text appeared in strange colours with several red dots at the top of the screen. It flashed white then returned to the strange Ubuntu text several times before the screen went blank. 

I'm really not great at all this, and my knowledge is terrible, but if anybody can see what's going on here, I'd greatly appreciate your help!

Cheers,

Biggs

Have you installed any hardware drivers for your video card? It sounds like a video issue. Go to system>administration>hardware drivers and see if there's a driver for your ATI card. If there is, install it.

---

### Post by abiggs on 2009-10-20
I tried and there wasn't any drivers for it. I should've added to the original post that now it's impossible for me to even enter the desktop screen, it just stops at the blank screen and no key combinations help. The only thing I can do from there is a hard off. I've tried starting in recovery mode and running fcsk and the auto graphic fix but no luck.

---

### Post by oboedad55 on 2009-10-20
> **abiggs said:**
> I tried and there wasn't any drivers for it. I should've added to the original post that now it's impossible for me to even enter the desktop screen, it just stops at the blank screen and no key combinations help. The only thing I can do from there is a hard off. I've tried starting in recovery mode and running fcsk and the auto graphic fix but no luck.

I should have asked, which version of ubuntu are you using? If you've got 9.04 give 9.10 a try. It's a beta but it's pretty well along and running well on my desktop.

---

### Post by abiggs on 2009-10-20
Yeah I'm using 9.04. Is there any way I can retrieve files from 9.04 first? I'll definitely check 9.10 out if it's running well.

---

### Post by P4man on 2009-10-20
Since you dont mention it, i assume vista is still booting ok?
If it is, try booting ubuntu in recovery mode, select a root shell and then type
```

dpkg-reconfigure xserver-xorg 
```
then reboot (just type reboot)

If that doesnt help try booting a livecd and use it to access your ubuntu partition (probably just in Places > Name of yourharddisk). Then browse further to /media/yourdrive/var/log/. There open a file called messages, and perhaps attach it to a post here.

---

### Post by abiggs on 2009-10-20
The first didn't work and I haven't installed Ubuntu to a partition, I just installed it to Windows. I tried anyway and I can only do the "try ubuntu without changing your computer' option, when I try from the hard disk it alerts me that host/ubuntu/disks/root.disk doesn't exist.

---

### Post by P4man on 2009-10-20
ah you did a wubi install.. then I dont know how to recover it im afraid :s

But is it possible you made the ubuntu virtual partition too small so its full now and thats why you're having problems? from the recovery console / root shell try this:

```
df -h
```

Is your / partition full or nearly full by any chance?

---

### Post by abiggs on 2009-10-20
I have absolutely no idea to be honest, I don't even remember assigning it to the partition. I'll give this a try though

---

