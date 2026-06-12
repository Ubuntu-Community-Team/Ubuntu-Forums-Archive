---
title: "dual boot troubles"
date: 2011-08-10
forum: General Help
---

### Post by p.wolf on 2011-08-10
hey all, just spent hours trying to set up a dual boot with windows 7 and ubuntu. i now have both installed, however, i dont know how to load ubuntu. it automatically loads windows 7 on boot. help please?

p.s both 64 bit if that matters.

---

### Post by xdominex on 2011-08-10
Did you install Windows second? If so, follow the instructions on this thread to reinstall GRUB to the MBR:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Hope this helps!

---

### Post by oldfred on 2011-08-10
You may not have to do the full purge & reinstall as posted above, but that should also work.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by p.wolf on 2011-08-10
i installed windows 7 first, i made sure to remove ubuntu then install windows 7, leaving space partioned for ubuntu, then i donwloaded and installed ubuntu alongside, this failed so i retried and reisntalled ubuntu, both should now be on my laptop,however, i only loads windows 7.

---

