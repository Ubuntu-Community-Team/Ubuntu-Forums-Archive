---
title: "Get rid of windows, Make ubuntu the only system."
date: 2010-01-17
forum: General Help
---

### Post by suffery on 2010-01-17
Well..I do not know how to start this off without sounding pretty stupid or like a complete idiot.
Im tired of windows basically. When i cruise the net it will get some kind of virus even though i had eset guarding my computer.
It got something called Omarik.OJ or something like that. Well i did a read and run me and after 6 weeks of non stop redirects I finally got the solution for it and solved it.
Well a week after everything stops working. Steam (im 16) quit working and nothing would open.
And as always having ubuntu as my back up system it of course worked like a charm.
I could cruise the Internet and do basically anything i wanted to. I even installed steam with wine just fine. I also installed KTorrent with no problems.
Now if i get CSS to work on Ubuntu then what reason do i actually have to have windows?
I hate windows.. The borders are tight and everywhere i go there is a hole in which i do not know about. 
Well, After that i naturally reset my system to factory default.
Well after the reset in the grub menu i chose windows like i usually would. Well it gave me a error about it being non existent yet i can mount OS just fine and cruise the new files written by the factory reset. And ubuntu remains. Over the last year i have learned more and more about ubuntu but im still a beginner. But i understand it a little better now.
(i keep going off topic, sorry)
But now the only system i have is ubuntu, But heres the thing. 
I have a 60gb hard drive. I only have 25gbs for ubuntu.
I want to delete windows completely and only have ubuntu. And if later in life i choose differently i can dual boot just like i use too.
How would i go in doing this?
I cant log in to windows. Only ubuntu.
I dont want to get rid of my ubuntu files but i will format and insert a cd to install ubuntu if i have to.
What procedure is needed to format? Can i completely dodge my ubuntu files? and add that portion of space to my ubuntu?
Thanks.
This forum has helped me a ton in the last year.

---

### Post by jamesisin on 2010-01-17
I use Ubuntu as my main machine.  I support all three major platforms (Mac, Windows, and Linux) and so I do keep machines (or Virtual Machines) running those operating systems.  Regardless, I am able to do all that I need to do on my Ubu box.

Is there some specific task you were concerned with being able to do?

---

### Post by fancypiper on 2010-01-17
You can probably use a partitioning tool to change your Windows partition(s) to a linux filesystem.

Post the results of this command and we will get started:

sudo fdisk -l

---

### Post by forsaken_pariah on 2010-01-17
Just use the Ubuntu LiveCD, fire up the partitioner, and delete the Windows partition, and resize the Ubuntu partition to take up all of the empty space.

You could install something to do this from the system on your hard drive, too, but I prefer editing partitions from outside of my main system.

Hope this helps...

---

### Post by suffery on 2010-01-17
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9c06833

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       10334    72774450    7  HPFS/NTFS
/dev/sda3           10335       14766    35600040    7  HPFS/NTFS
/dev/sda4           14767       19457    37680457+   5  Extended
/dev/sda5           19132       19435     2441848+  83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris
/dev/sda7           14767       18946    33575787   83  Linux
/dev/sda8           18947       19131     1485981   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         488     3919841    b  W95 FAT32

Alrighty, Heres the results.
What do i do now?

---

### Post by baddog144 on 2010-01-17
The best thing to do would probably be to use the Partition Editor on the livecd. That will make it fairly clear which are Windows partitions and which are linux partitions, and you  should be able to  delete the windows  ones and resize your linux partitions to fill that empty space

---

### Post by lev-unr on 2010-01-17
You could try to run the gparted system and only delete the windows partition and make it into some sort of storage system or whatever. It would also allow you to change your mind. 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by jamesisin on 2010-01-17
> **forsaken_pariah said:**
> You could install something to do this from the system on your hard drive

You can't unmount an active partition so you'll want to do this from the live CD or from a gparted CD (both will allow re-partitioning).  Back up your data first in case there is a problem with the repartitioning.

---

### Post by fancypiper on 2010-01-17
You need to change these 4 partitions to whatever you desire:

/dev/sda1 1 1274 10233373+ 12 Compaq diagnostics
/dev/sda2 * 1275 10334 72774450 7 HPFS/NTFS
/dev/sda3 10335 14766 35600040 7 HPFS/NTFS
/dev/sdb1 1 488 3919841 b W95 FAT32

Boot with your Ubuntu install CD and you should be able to use GParted (System>Administration>GParted) to manipulate those partitions to what you want/need.

Don't forget to read that fine manual that is provided under the help menu.

---

### Post by suffery on 2010-01-17
Alrighty. Im in the boot live cd.
Im in the gpart program.
Now what do i do? Do i format to linux swap or something else?
The flags on /dev/sda2 is boot
Its file system is ntfs and the label is OS. This is the main thing i need switched to ubuntu.
Thanks :)
 /ded/sda2 contains windows files along with the boot. as it says in the flag.
But my ubuntu is in sda7. What do i format os to, if im going to increase the linux size.
And once i format. How do i add that space to ubuntu. It wont let me make it any bigger when i try to resize

---

### Post by fancypiper on 2010-01-17
I don't think you need any more swap. If you want to change /dev/sda2 only, I would choose an ext2, ext3 or ext4 (default for Ubuntu 9.10) filesystem.

I think you may have to re-install grub after changing it.  What release are you running?

If you don't know, open a terminal anc command:
**lsb_release -a**

---

### Post by jamesisin on 2010-01-17
What is on 4, 5, 6, and 8?

Which file system is on 7?  (My guess would be ext4.)

---

### Post by fancypiper on 2010-01-17
> **jamesisin said:**
> What is on 4, 5, 6, and 8?

Which file system is on 7?  (My guess would be ext4.)/dev/sda4 is an extended partition that contains /dev/sda5, /dev/sda6, /dev/sda7 and /dev/sda8 (which is swap) partitions. See OP post of fdisk -l output.

The command **mount** will tell what file system each contains.

---

### Post by jamesisin on 2010-01-17
You're saying that 4 consists of 5, 6, 7, and 8?  I don't use Extended partitions, so I'm asking because I don't understand.

As to the swap and so forth, I can read the table well enough.  I am asking because it looks like two Linux installations each with its own swap partition.  If that's the case, this will inform next-steps.  If it's only one Linux installation, why is it set up in this manner?

He has a number of options, I'm just trying to tease out which are the best for his particular situation.

---

### Post by suffery on 2010-01-17
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

I have no idea why theres that many earthier, It must have did it automatically.
I only have one ubuntu version.

---

### Post by fancypiper on 2010-01-17
Please excuse the sidetrack, suffery.

[Linux Partition HOWTO]("http://tldp.org/HOWTO/Partition/")

I don't understand the OPs partitioning scheme either.

I keep mine simple with /, swap, /home and /pub partitions on my main drives, but I tossed Windows in 1999 and with my 4th computer upgrade, I settled on my scheme.

```
Sun Jan 17 01:15 AM root@tinwhistle ~ # fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee220

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2612    20980858+  83  Linux
/dev/sda2            2613        2874     2104515   82  Linux swap / Solaris
/dev/sda3            2875      121601   953674627+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfafc581b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
Sun Jan 17 02:48 AM root@tinwhistle ~ # mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
/dev/sdb1 on /pub type ext4 (rw)
/dev/sda3 on /home type ext4 (rw)
Edited for clarity

```

---

### Post by fancypiper on 2010-01-17
Here is the guide to re-install grub2:

[How to restore Grub from a live Ubuntu cd](http://ubuntuforums.org/showthread.php?t=224351)

It might be easier for the OP to use the 2nd hard drive for storing the /home folder (format as ext4) and do a fresh install with a better partitioning scheme.

---

### Post by jamesisin on 2010-01-17
That sounds like a strong plan.  First wipe and partition the second drive as ext4 then make a copy of /home over there.  Next wipe all partitions from the main drive and create a minimal partitioning scheme with a basic installation (including grub) on that drive.  Finally either restore the /home from the backup or point the new installation to the /home on the second drive.

---

