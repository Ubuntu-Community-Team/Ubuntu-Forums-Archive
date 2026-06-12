---
title: "Delete Windows partition"
date: 2010-07-09
forum: General Help
---

### Post by eduine on 2010-07-09
Hi everybody!
I've a computer with, recently installed ubuntu 10.04 lucid lynx.
My problem is that i want to delete my windows vista's partition, and grub.
After that i would like to expand my linux partition with the new empty space.
I will after that have my computer automatically booting on my only partition : linux!

But i don't know how to delete the partition and grub without creating boot problems...
And i'm a recent user of linux, so i'm not very comfortable with the Konsole.
If anyone could help me, it will pleased me a lot!

And sorry for my bad english... I'm french ^^

---

### Post by ajgreeny on 2010-07-09
If this was a normal ubuntu install using separate partitions, and not using wubi to install ubuntu inside windows, you should be able to delete the Vista partition using gparted, either from your ubuntu live CD or even from your installed ubuntu OS without it causing any problem to grub, as grub itself is normally on the MBR of the hard disk, and all the config files for grub are on the ubuntu OS partition.

Should that not be the case, you can always restore grub with the live CD, so no need to worry about that.  After deleting the windows partition, and hopefully booting to ubuntu without a problem, just run ```
sudo update-grub
```and windows will be removed from the grub menu automatically for you.  The unallocated space of the old windows partition, can either be added to your ubuntu partition, or perhaps more easily just used as a separate /data partition mounted at boot with an edit to your /etc/fstab file.

If you do want to add the free space to the current ubuntu partition, use a live CD, and assuming windows was first on the disk, just grab the left hand end of the partition and move it all the way left, to fill the space.  This will take a long time depending on the size of your current ubuntu install and the files on that partition, as in effect the partition and all files and folders will have to be checked, then copied and moved, and then the new partition will be checked again.  That can take a couple of hours on a big partition.

The choice is yours!

---

### Post by mike555 on 2010-07-09
You can boot into Ubuntu ,install gparted , then in gparted pick the Windows partition and format (erase) it ,making it a ext4 file format ... then just use that partition for backup ... 
   after doing that be sure to type in terminal " sudo update-grub " without the quote marks ... 
   then it should boot into Ubuntu from Grub (you need grub to boot Ubuntu),you can install startup manager and in it set grub time to something like 3 seconds or even less if you want .. 

   Later assuming that worked well for you you can delete the backup partition ,if you want and expand Ubuntu .. afterwards doing another sudo update-grub ... but I would use it as backup ..

---

### Post by RJ12 on 2010-07-09
Also make sure that if you put the space in the Ubuntu partition run sudo update-grub before you reboot so it detects the new UUID of that partition and updates the GRUB config. accordingly.


I also think the space should be used as a separate backup partition. It is a good idea, and could save headaches in the end.

:p

---

### Post by eduine on 2010-07-13
thank you  all!
I was afraid to erase my windows partition because i had problems deleting ubuntu partition with grubs...
But i didn't know that grub's files were on my ubuntu part!
So i decided to keep my ex-windows part as a backup one, it's really easier!
Thanks again! and if your bored, look at this thread : [http://ubuntuforums.org/showthread.php?t=1530114](http://ubuntuforums.org/showthread.php?t=1530114)

^^ bye!

---

