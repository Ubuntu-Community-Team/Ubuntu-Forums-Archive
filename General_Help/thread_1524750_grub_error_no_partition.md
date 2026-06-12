---
title: "grub error no partition"
date: 2010-07-05
forum: General Help
---

### Post by WakingTheCadaver on 2010-07-05
Hi all. I recently got a laptop  so i had to get rid of ubuntu off my computer (ubuntu/windows partition). So i looked on the internet and they said go into windows disk managment or something like that. So i did and i deleted the ubuntu partition but now when i load up my computer it comes up as 
No such partition
Grub rescue

So i talked to my friend and he said make a usb live disk and resize the partition to one big one so i did and i still have the problem.

Please help

---

### Post by drs305 on 2010-07-05
Welcome to Ubuntu and the Ubuntu forums!

I'm not clear on what you are attempting to do. Do you currently only have Windows on your machine and it won't boot? The reason for that would be that grub is still on the MBR and Windows can't use it. To restore Windows, refer to this link:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

Go to the section: How to Restore the Windows ___ (XP or Vista/7) Bootloader.

---

