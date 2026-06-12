---
title: "Problem overwriting old Windows Partition with Linux (Ubuntu 11.10)"
date: 2012-04-14
forum: General Help
---

### Post by Nero60 on 2012-04-14
I was operating in a Dual Boot mode.  Since I no longer required the Windows XP O/S, I attempted to expand Linux partitions to overwrite the old Windows partitions.  It appears that the procedure was somewhat successful since the Windows O/S does not appear in the O/S list.  However, at the Ubuntu start page, I receive the following information:

      "The disk drive for /home is not ready yet or not present"

      "Continue to wait, or Press S to skip mounting or M for manual 
       recovery"

Pressing "S" starts the operating system.

I've checked an d determined that the original NTFS partition has been formatted to Ext3 and the following entry is valid "/dev/hda1 /home ext3 defaults 0 0.

Please help!

Nero60

---

### Post by UltimateCat on 2012-04-14
If you can open the terminal try posting the output to all the partitions listed and it will help us to see what is going on.

```
sudo fdisk -l

```

Did you want  to resize or shrink your Windows partition?

Or did you want to delete your Windows partition all together and allow Ubuntu 11.10 full access?

---

### Post by agillator on 2012-04-14
Some specific things to look at (the fdisk command above should answer some):

Is /home on a separate partition (or separate disk for that matter)?

If so, check /etc/fstab to see how that partition is referenced. Is it /dev/sda(x) or is it a UUID (a long string of hexadecimal). If it is the /dev/sd.... reference, the partition number probably was changed when you changed the structure and you need to change the reference in fstab. If the reference is a UUID then we will need to check a little deeper, or perhaps create a new UUID for it.

But do post the results from fdisk -l please. That is a good place to start.

---

### Post by Nero60 on 2012-04-16
The following is the output from sudo fdisk -l



Disk /dev/sda: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x6edd6edd 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   107025029    53512483+  83  Linux 
/dev/sda2       140086800   156296384     8104792+  49  Unknown 
/dev/sda3       107025030   138608819    15791895   83  Linux 
/dev/sda4       138608820   140086799      738990    5  Extended 
/dev/sda5       138608883   140086799      738958+  82  Linux swap / Solaris 

Partition table entries are not in disk order 

I would like to do away with Windows partition and utilize it for Ubuntu 11.10

Thanks in advance for your help.

---

### Post by Nero60 on 2012-05-10
I would very much like to update Ubuntu 11.10 to Ubuntu 12.04 LTS but am concerned since I have not been able to correct above partition problem.  Can someone help me out!

---

