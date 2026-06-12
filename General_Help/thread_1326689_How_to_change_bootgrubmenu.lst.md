---
title: "How to change boot/grub/menu.lst"
date: 2009-11-14
forum: General Help
---

### Post by Ancient Dragon on 2009-11-14
I am dual booting Windows 7 and Ubuntu 9.  Previously had openSUSU but overwrite it with Ubuntu because I didn't like it.  Now when I boot the computer I get a grub menu with too many options.  I'd like to clean it up so that the only options I have is either Ubuntu or Windows 7.  I know I can't just change menu.lst and have tried "sudo update-grub".  Isn't there a file somewhere that I can change to clean up that menu?

Thanks

Melvin

---

### Post by mikewhatever on 2009-11-14
Here's a good guide -> [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

You have two OSs, Ubuntu and Windows, so which entries do you want to get rig of?

---

### Post by Ancient Dragon on 2009-11-14
Thanks for your reply.  The menu shows about 9 entries -- 4 for Ubuntu, 3 for Windows 7, and 2 for openSUSU.

---

### Post by mikewhatever on 2009-11-14
I am curious, do you have separate partitions with various Windows versions? And how can update-grub still pick up Open Suse, if you'd formatted the partition and installed Ubuntu?

Anyway, what I did to get rid of unneeded entries, was this:
[list]copying the Windows entry I wanted to keep from /boot/grub/grub.cfg to /etc/grub.d/40_custom to make it a permanent custom entry

adding 'GRUB_DISABLE_OS_PROBER=true' to /etc/default/grub, to prevent grub looking for other OSs beyond root

runnign sudo update-grub[/list]

---

### Post by mick55 on 2009-11-14
Hi AncientDragon

> I know I can't just change menu.lstSure you can.Open a teminal and run this command
```
gksudo gedit /boot/grub/menu.lst
```Remove or comment out  the entries you dont need.
Make a backup first if you're uncomfortable editing the file.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

---

