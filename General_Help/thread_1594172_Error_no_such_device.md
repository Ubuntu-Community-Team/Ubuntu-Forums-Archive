---
title: "Error: no such device"
date: 2010-10-12
forum: General Help
---

### Post by Eildor on 2010-10-12
I decided to go ahead and try out Ubuntu for the first time (never used a Linux OS before) ...it hasn't gone well to say the least.
 
I downloaded the wubi installer and installed the netbook version of Ubuntu (10.04). It was installed on my Samsung NC10, where Windows XP installed on a small partition and program files were kept on the other larger partition. Ubuntu was installed onto the larger partition.
 
After booting into Ubuntu there were some updates which came up, so I went ahead and and let it update... after that it needed to restart -- and from there things have never been the same :( I now get a "Error: no such device <enter some random letters and numbers here>" error. 
 
I tried googling the solution but haven't managed to get anything to work. I put Ubuntu onto a USB and so I can get into that "live" Ubuntu; I've tried all sorts of strange and meaningless (to me, anyway) commands in Terminal... nothing has worked. I even went into the drive and deleted Ubuntu thinking that perhaps that would stop it trying to load Ubuntu but that didn't work either -- probably not a good move, but I'm desperate.
 
Right now, I'd be quite happy to just fix Windows and forget about Ubuntu. I really need to get this sorted within the next 3 hours before Uni.
 
I'd appreciate your help guys. Please also remember I'm new to Ubuntu, I wont understand you if you give technical and advanced instructions.

---

### Post by P4man on 2010-10-12
This is a (accidental?) wubi install I bet; you installed from within windows, and on to a windows partition (even if you made one for ubuntu, which may have contributed to the problem). I strongly recommend not doing that and do a real dualboot, which means you boot from usb or cd in to a live session and run the installer from there. Thats the only way to install ubuntu on a native filesystem. Wubi is.. well, a hack.

Anyway, the fix isnt hard. You need to fix windows bootloader and you can do that by booting a windows cd. Depends what version of windows you have though.

alternatively, this fix for 9.10 probably still works, though I have heard it only works for a single boot:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If you cant boot in to windows do it from the live cd.

---

### Post by Eildor on 2010-10-12
I'm using a NC10 and therefore I have no CD drive. I have put Windows XP onto a USB, however it doesn't seem to give me the recovery option. It does however give me a list of partitions (more than I actually have...) and selecting one of them enables me to log into Windows XP.
 
So, I'm now in Windows XP (can only get into XP using the USB stick). What can I do now that I am in Windows XP to fix the problem?

---

### Post by P4man on 2010-10-12
I think you  need a recovery console, I dont think the command is available from a regular login but im unsure what is you have. From a XP recovery console run

```
fixboot
```

and/or

```
fixmbr
```

---

### Post by Eildor on 2010-10-12
I don't have a CD drive or a Windows XP CD. I have a Samsung NC10 -- the Windows XP installation disk is not provided.

---

### Post by P4man on 2010-10-12
I thought you had windows on a usb stick?
Anyway, if you dont have a windows recovery console, then you can try to write the windows bootloader from the ubuntu livecd. Boot it, open a terminal and type:
```

sudo apt-get install ms-sys 
```

(requires internet connection)

Next, check the letter for your windows drive; I assume its /dev/sda but check in system > administration > disk utility

then rewrite the windows bootloader:

```
sudo ms-sys --mbr /dev/sda 
```

replace sda with the appropriate drive.

reboot.

---

### Post by Eildor on 2010-10-12
Yes I have Windows on a USB stick but it doesn't seem to allow me to boot from it. All it does is gives me a list of different partitions. I've already tried the above and they do not work.
 
This is such a nightmare.

---

### Post by P4man on 2010-10-12
sorry.. looks like ms-sys is no longer available due to copy right violations. And hasnt been for some time.

As for that windows stick presenting a list a partitions, I dont quite get it what that is, you will have to be more clear. Isnt there a recovery mode? Is this an installation stick or what?

---

### Post by Eildor on 2010-10-13
Ok I managed to get into the Recovery Console. I tried fixboot and fixmbr. Still not fixed.

---

### Post by P4man on 2010-10-13
I have no idea what you did in the first place then. Rather than guessing, please download and run this bootinfoscript from a live session:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

and upload the results so we have some idea of whats going on.

---

### Post by Eildor on 2010-10-13
Ok thanks for trying. I've spent way too much time on this so I'm just going to format my hard drive and reinstall Windows.

Thanks anyway

---

