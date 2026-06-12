---
title: "ERROR 15 and all partition widhout any files"
date: 2009-10-29
forum: General Help
---

### Post by edup_pt on 2009-10-29
Hello,

Im depared with a critical problem (for me). Im getting error 15. After searching the usual foruns and threads for this error im depared with this cenario:

- I mount all the partitions
- I make "ls -laht" and the result is:

   /dev/sda2(root): Only some directorys and files, but No /var/log, no /etc, no /boot, no lost+found, no /usr etc, etc....

 The other partitions are empty.

 I thought that i was attacked with a "rm -rf" (to be sincerly i dont know what is the interest of this people anyaway).

 But when i run the ubuntu live cd and run the application gparted it shows me that i have used space in all partitions(600Mb, 300Mb, 3GB).... So its data there, i believe.

The problem is that when mounted, there is no data.

I run the fsck.ext in all and every partitions results in clean. Now i have lost+found in every partitions, but empty directory. 

So i have an empty partitions but with a used space.

I have a lot of important data in the disk so can you please give me some clue? 

Thanks to all trys.

Best Regards,

Eduardo

---

### Post by tempus on 2009-10-29
I had the same error 15 message and ended up reinstalling 9.10 from scratch. I tried several things suggested and it did not work. There seems to be an incompatibility between the grub loaders.:popcorn:

---

