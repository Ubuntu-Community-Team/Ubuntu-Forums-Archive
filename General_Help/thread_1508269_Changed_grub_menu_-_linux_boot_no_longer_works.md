---
title: "Changed grub menu - linux boot no longer works"
date: 2010-06-12
forum: General Help
---

### Post by DaybreakBoy on 2010-06-12
Hi there,

My computer has windows and (I think) Jaunty installed on it, but a couple of weeks ago I was trying to change something (update maybe? I don't remember)and I changed something in my grub menu.

Now when I get the menu when I turn the computer on the windows option works but the linux one doesn't.  What I think actually happened is that I updated linux to koala (?) but chose the option not to change the grub menu (thinking this would keep my dual boot settings), which means that grub menu is pointing to an old install of linux.  

Anyway, is there anyway to fix this?  What I'd ideally like is to install the latest version (Lucid) on whatever partition has already got linux on it and keep my windows install as well. 

I would just go full linux cos it's so much quicker but I've had problems in the past with getting wireless to work, also sound cards.  So I want  to keep the windows install as a back up while I sort those issues. Anyway.

Also, I don't have a cd player...

Any help at all would be much appreciated.

[EDIT]  So I can change the grub menu from the menu itself, I just need to know what the path is to boot linux, now I'm pretty sure I installed Koala on D:, any hints?

---

### Post by DaybreakBoy on 2010-06-12
bump

---

### Post by dcstar on 2010-06-12
> **DaybreakBoy said:**
> Hi there,

My computer has windows and (I think) Jaunty installed on it, but a couple of weeks ago I was trying to change something (update maybe? I don't remember)and I changed something in my grub menu.
........
[EDIT]  So I can change the grub menu from the menu itself, I just need to know what the path is to boot linux, now I'm pretty sure I installed Koala on D:, any hints?

Search for the Grub2 reinstallation instructions.

---

### Post by DaybreakBoy on 2010-06-12
Thanks, will do.

---

### Post by Dn4mycrownj on 2010-06-13
here you go     [http://https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("http://https//help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by oldfred on 2010-06-13
You should be able to manul boot:

Manual boot:
#show you the available partitions
ls
#look for boot files on the partitions
ls (hd0,1)/boot
# continue until you see vmlinuz-2.6.xxxx
#then boot that linux replacing hd0,1 with your partition
insmod ext2
set root=(hd0,1)
# in the next command sda1 represents (hd0,1), sdb2 would be for (hd1,2)
linux /vmlinuz root=/dev/sda1 ro quiet splash
initrd /initrd.img
boot
Install grub to MBR:
sudo grub-install /dev/sda
sudo update-grub

General info:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

