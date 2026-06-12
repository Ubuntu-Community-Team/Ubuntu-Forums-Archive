---
title: "Speed up *even more* 12.04 boot time ?"
date: 2012-04-28
forum: General Help
---

### Post by GameX2 on 2012-04-28
Hi!


I did a fresh install of 12.04 LTS and I'm very satisfied with it. :)
I was wondering if it was possible to speed up *even more* the boot time ? :P

Just for the sake of it, I compared the boot speed of Ubuntu and Windows 7, using autologin and loading YouTube.  That was a close one, Ubuntu finished just 3 seconds before Windows.

What I find strange a bit, is that Ubuntu take a bit of time to load on GRUB (like 10 seconds).  The GRUB background image is still there, then when the Ubuntu logo arrive, it's blazing fast.  Anyone else got this delay on the GRUB screen?
As for Windows 7, when I select the entry in GRUB, GRUB load Windows automatically.  Is there a reason for that?  Because my Windows partition is the first on the disk?

I found some tricks to speed up the boot time (like applying a profile to GRUB), but I don't know if they work with 12.04 (The developpers really worked hard to make it boot faster than ever).

I'm using a 64-Bits version, I've got 8 GB of RAM. :)

Thanks!

---

### Post by Barhilton on 2012-05-11
I also have the problem with the GRUB screen. Anyone know why/how to fix it?

---

### Post by Enigmapond on 2012-05-11
You can try running this command in the terminal. All it does is makes all the startup apps appear in startup applications.(by default it just lists things that you put in there) Then just turn off what you don't use right away. I found I cut the boot-time in half.

```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

---

### Post by Zvlwab on 2012-05-11
The file /etc/default/grub contains the following line:
```
GRUB_TIMEOUT=10
```

This is the time it takes before it boots the first selected OS.

Just edit that number, save and run
```
sudo update-grub
```

This will change the waiting time in GRUB.

I'm not sure if this is what you meant, but you can make your computer boot 10 seconds faster this way. (Or 9 if you want to be able to select another OS)

---

### Post by nermal0 on 2012-06-20
> **Enigmapond said:**
> You can try running this command in the terminal. All it does is makes all the startup apps appear in startup applications.(by default it just lists things that you put in there) Then just turn off what you don't use right away. I found I cut the boot-time in half.

```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

Great tip, thanks for posting this!

---

### Post by Jvdy on 2013-01-12
using all CPU Cores during boot

sudo gedit / etc / init.d / rc

edit line like this

[HTML]CONCURRENCY=makefile[/HTML]

or 

```
CONCURRENCY=none
```

replace with 

[PHP]CONCURRENCY=shell[/PHP]

---

### Post by oldos2er on 2013-01-12
CONCURRENCY=shell is obsolete, stick with CONCURRENCY=makefile.

---

