---
title: "What to do when things go wrong?"
date: 2011-06-20
forum: General Help
---

### Post by ligiopro on 2011-06-20
It's my second day on ubuntu and I've managed to corrupt my filesystem twice already, both times after a hard reboot. Couldn't repair the filesystem with an Ubuntu live cd and had to use a slitaz live cd instead, but at least that got ubuntu booting again. I'm using 10.04.

The main issue is I don't know what to do after something goes wrong. ie. system freezes, no response to user input or GUI goes black and only the cursor is left but responsive. 
What keys should I press to try and recover (like CTRL ALT DEL in windows)?
As well, is there a way to repair my linux partition from within windows xp?

---

### Post by hwttdz on 2011-06-20
alt+ctrl+f[1-6] will get you to the different tty's.  i.e. a command line.  

Though it sounds like you're having a bigger problem.  If you're using ext4 (which should be the default), the disk checking only takes a minute.  So it's possible there's a hardware error (i.e. bad hard disk).  You might want to look into the SMART status of the drive.

---

### Post by haqking on 2011-06-20
> **ligiopro said:**
> It's my second day on ubuntu and I've managed to corrupt my filesystem twice already, both times after a hard reboot. Couldn't repair the filesystem with an Ubuntu live cd and had to use a slitaz live cd instead, but at least that got ubuntu booting again. I'm using 10.04.

The main issue is I don't know what to do after something goes wrong. ie. system freezes, no response to user input or GUI goes black and only the cursor is left but responsive. 
What keys should I press to try and recover (like CTRL ALT DEL in windows)?
As well, is there a way to repair my linux partition from within windows xp?


If i hadnt screwed up my machine or others ;-) i wouldnt know anything.

as long as it is not a corporate or operational machine, then every screw up is a lesson ;)

I thirve off screwing things up..LOL

---

### Post by coffeecat on 2011-06-20
Welcome to the forum.

You need the magic keys when/if your system seizes up and you need to shut it down gracefully. See:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Remember R-E-I-S-U-B, "busier" backwards and you'll be OK. Also, on some keyboards/systems, you need to use the AltGr key (to the right of the keyboard) rather than the Alt key.

No, you can't repair a Linux filesystem in Windows. You need a Linux live CD. What was the problem with the Ubuntu CD?

---

### Post by mcduck on 2011-06-20
In addition to the magic keys above, you can also use *SysRq+k* to kill all the processes running on current virtual console. Doing this from the desktop would kill all your programs and restart the desktop, throwing you into the login screen.

Works a bit smoother than a full reboot if it's just a case of a frozen desktop or graphical application and the system is still otherwise working fine.

---

### Post by ligiopro on 2011-06-20
> **coffeecat said:**
> 
No, you can't repair a Linux filesystem in Windows. You need a Linux live CD. What was the problem with the Ubuntu CD?

I tried running fsck and e2fsck with sudo, but I couldn't get r/w access to the partition even though it wasn't mounted. e2fsck worked like a charm in slitaz (maybe because i was running a root account? i though sudo and root were pretty much equivalent).

---

### Post by coffeecat on 2011-06-21
> **ligiopro said:**
> I tried running fsck and e2fsck with sudo, but I couldn't get r/w access to the partition even though it wasn't mounted. e2fsck worked like a charm in slitaz (maybe because i was running a root account? i though sudo and root were pretty much equivalent).

Puzzling. "sudo fsck" *should* have worked. Another way of filesystem checking in the Ubuntu CD, although it doesn't give you control over fsck options, is to open Gparted, right-click on the partition and select "check".

---

