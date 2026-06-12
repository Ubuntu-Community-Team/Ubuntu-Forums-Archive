---
title: "Help! System shows weird statements at startup!"
date: 2011-02-15
forum: General Help
---

### Post by LambFollower on 2011-02-15
I have recently installed Ubuntu on my system.(around 20 days ago). I have installed it separately to windows.(ie. I can access either Windows or Ubuntu).

Today, I turned on the PC. The usual Intel display screen showed up.After that, a black background appeared with the following statements:


error: file not found.
grub rescue>


What does this mean?
What sort of commands should I input?

Thank you

---

### Post by sanderd17 on 2011-02-15
Probably, there is nothing wrong with your files and settings. so before you try to fix it, make a BACKUP of your entire computer using a live CD.

What you need to do is reinstall GRUB. You can google for it, but I think that point 13 in the thread [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) will help you.

---

### Post by sanderd17 on 2011-02-15
I forgot to mention. If you google it, make sure that you seach for GRUB 2, if the post is older than 2010 and no number is given, it will likely handle GRUB Legacy and not GRUB 2.

---

### Post by LambFollower on 2011-02-15
Could this be because of applying the "Permanent Fix" from the Wubi Megathread [http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi+megathread](http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi+megathread) (I later realized that my installation was not a Wubi one).

Thank you

---

### Post by Kirboosy on 2011-02-15
Yes that is very likely why GRUB has taken a turn for the worst.

---

### Post by sanderd17 on 2011-02-15
Let me explain the commands you executed:
move the GRUB files to another directory as backup:
```

sudo mv /boot/grub /boot/grubold

```
make a new empty direcotry as a "fake" grub (wubi doesn't need grub):
```

sudo mkdir /boot/grub

```
copy the some settings (don't ask me what settings) to the new grub folder:
```

sudo cp /boot/grubold/grubenv /boot/grub

```
reconfigure grub:
```

sudo update-grub

```

So what you need to do is boot a live CD, open nautilus in root mode
```

gksudo nautilus

```
open the ubuntu partitiom, delete /boot/grub and change the name of /boot/grubold to /boot/grub

afterwards you will need to run
```

sudo update-grub

```
to reconfigure grub again.

I hope this will work.


Some additional info:

the sudo commands like sudo, gksudo and gksu give you root rights. If you have to use those commands, you will probably change something important to your system.

GRUB stands for GRand Unified Bootloader, it's the program that runs when your computer is started and lets you choose which OS to start. Wubi uses the bootloader from windows.

---

### Post by LambFollower on 2011-02-18
Hello. Thank you for the reply. I found "/boot/grub", but there is no "/boot/grubold", what should I do? Should I delete /boot/grub anyway?

---

### Post by lordjj on 2011-02-18
Hey LambFollower.
Do this:
-Boot from Live CD 
-Delete /boot/grub/ from the Filesystem
-Open Terminal, and input:
```
 sudo fdisk -l
```
 look for "Linux" in the "Filesysytem" column
 note the corresponding  "sdXY" (where X is a letter and Y is a number; e.g: sda1 or sda5...)
then do this: (replace sdXY with the right one)
```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
sudo umount /mnt
```
And reboot. ;)

---

