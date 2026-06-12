---
title: "Wubi GRUB files broken (11.04)"
date: 2011-05-04
forum: General Help
---

### Post by jcracken on 2011-05-04
Hi, I have made a huge mistake recently, and need a way to fix my GRUB. Recently, I stumbled across an alternate bootloader called Burg. Following the instructions on their website ([http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)) I installed it over my wubi grub files. I overwrote the wubildr file on my C:/ drive, even though I had installed Ubuntu on G:/ and the rest of my files were there. I booted into GRUB, and it went straight to the command prompt recovery mode. I booted back into windows, and overwrote the new wubildr with the one in the winboot directory under Ubuntu on G:/. Then, no matter what I did afterwards, it would flash on the screen: 
```
Error:File Not Found 
Error:File Not Found
Error:File Not Found
Error:File Not Found
```
then go straight back to the Windows Bootloader. I tried to remedy this by using system recovery in Windows to restore the original file. However, now when I boot into GRUB, it asks for a system disc. I am afraid that this will just overwrite my original installation, which I do not want to do. If this is the only choice, I would like to retrieve some important documents from the Wubi partition before deleting everything.

Thanks,

---

### Post by bcbc on 2011-05-04
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) has a tool that can read the root.disk from windows.

If you want an explanation of how Wubi boots:
1. entry in BCD/boot.ini to call wubildr.mbr (any location) - this is grub4dos
2. wubildr.mbr searches for wubildr in the root of any partition (usually finds it in C:\wubildr)
3. wubildr searches for and finds the file \ubuntu\disks\root.disk on any partition. First one it finds it loop mounts and presents the /boot/grub/grub.cfg file (the grub menu).

Don't know if that will help - no idea what your system restore did.

---

### Post by jcracken on 2011-05-04
> **bcbc said:**
> [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) has a tool that can read the root.disk from windows.

If you want an explanation of how Wubi boots:
1. entry in BCD/boot.ini to call wubildr.mbr (any location) - this is grub4dos
2. wubildr.mbr searches for wubildr in the root of any partition (usually finds it in C:\wubildr)
3. wubildr searches for and finds the file \ubuntu\disks\root.disk on any partition. First one it finds it loop mounts and presents the /boot/grub/grub.cfg file (the grub menu).

Don't know if that will help - no idea what your system restore did.


THANK YOU SO MUCH! You have no idea how much you helped me. I'm thinking of re-installing Ubuntu all together, but through an actual LiveUSB. I had previously tried the program, but had no idea how to use it. With your help, I was able to access all my files. You are a life-saver.

---

