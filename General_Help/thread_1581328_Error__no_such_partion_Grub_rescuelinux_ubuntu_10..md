---
title: "Error : no such partion: Grub rescue:linux ubuntu 10.4"
date: 2010-09-24
forum: General Help
---

### Post by Mwanitete on 2010-09-24
Hii friends
 
I make a mistake in my ubuntu linux 10.4
 
when I boot it agai it says Error : no such partition Grub resscue
 
So I would Like to Go back to my window vista and install linux again by using wubi installer...
 
So how how can I start my window vista when I have such problem
 
Need help friends..please help me i am dead
 
Jeff

---

### Post by andrewthomas on 2010-09-24
you don't need to install with wubi.

Just read this post.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by bcbc on 2010-09-24
> **Mwanitete said:**
> Hii friends
 
I make a mistake in my ubuntu linux 10.4
 
when I boot it agai it says Error : no such partition Grub resscue
 
So I would Like to Go back to my window vista and install linux again by using wubi installer...
 
So how how can I start my window vista when I have such problem
 
Need help friends..please help me i am dead
 
Jeff

If you installed with wubi, and when you boot the first thing you see is the grub rescue, then this means you installed grub to your drive MBR. This doesn't work with Wubi installs which rely on the windows bootloader.

So to fix, use your windows repair disk to reinstall the windows bootloader:
winxp use command: fixmbr
vista/7 use command: bootrec.exe /fixmbr

This will get both windows and (wubi) ubuntu  booting again. Next time you update grub-pc take care not to install it to any devices.

If you don't have a windows disk you can boot an Ubuntu live CD/USB and install the lilo bootloader to act the same as windows' bootloader:
```
sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
```

You will get warnings after installing lilo, which you can safely ignore as it refers to the use of lilo for booting linux.

---

