---
title: "Partition table gone???"
date: 2010-01-21
forum: General Help
---

### Post by amaroKer on 2010-01-21
I've been trying to fresh upgrade to 9.10 from 8.04 and add XP to a dell box.  I got new ubuntu installed and working properly, then got XP on, installed, and updated.  When I tried to reinstall GRUB, by Ubuntu install could not find my /home partition (/dev/sdaX, cannot remember what X was) and would not boot.  **Gparted from the 9.10 live stick now only shows my entire drive as unallocated**, but
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1310    10482412+   7  HPFS/NTFS
/dev/sda3            1311        2224     7341705    5  Extended
/dev/sda4            2029        2224     1574370   82  Linux swap / Solaris
/dev/sda5            1311        2028     5767272   83  Linux

Disk /dev/sdb: 2029 MB, 2029518848 bytes
243 heads, 32 sectors/track, 509 cylinders
Units = cylinders of 7776 * 512 = 3981312 bytes
Disk identifier: 0xc3072e18
```
My /home partition is not in the extended and, as such, is lost.  I think that reinstalling GRUB did something to the partition table (???), and that it must still be rescuable.  Any help appreciated.

---

### Post by flabdablet on 2010-01-21
It won't be the GRUB reinstall that did the dirty deed - it will be the Windows setup disc. Windows has very fixed ideas about how partitioning should be done, and its setup code is ruthless in enforcing these. That's why I always recommend that if you're setting up a dual-boot machine with Windows, you do the Windows install **first**. This also saves needing to reinstall GRUB.

Assuming your /home partition was supposed to be a logical partition starting on cylinder 2225 and ending at 9725, it's unlikely to have come to actual harm. Try```
sudo cfdisk /dev/sda
```
You should see a bunch of free space at the end of the drive. Make a new logical partition in there (accept the default for the size, and cfdisk will fill it all). You'll find that the new partition will be /dev/sda6, and that /dev/sda3 will be expanded to make it fit. You'll also find that the partition type defaults to 83, which is probably what you want. Write the partition table out and quit cfdisk, then do```
sudo e2fsck -n /dev/sda6
``` to make sure the filesystem is still OK.

I like cfdisk for this kind of job, because it's very good at making correct partition tables and *doesn't attempt to do anything except* be very good at making correct partition tables. In particular, it will *never* make filesystem changes of any kind.

---

### Post by amaroKer on 2010-01-22
Thanks for the reply.  My sda6 (/home) is a primary partition.  The extended partition size is all accounted for by sda's 4 and 5.  Does this change the situation?

---

### Post by amaroKer on 2010-01-22
```
cfdisk (util-linux-ng 2.16)

                              Disk Drive: /dev/sda
                        Size: 80000000000 bytes, 80.0 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 9726

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1                    Primary   Dell Utility                        41.13
    sda2        Boot        Primary   NTFS             []              10734.00
                            Logical   Free Space                           0.01*
    sda5        NC          Logical   Linux ext3                        5905.76*
    sda4                    Primary   Linux swap / Solaris              1612.16
                            Logical   Free Space                       61706.06


```

Won't create parition, says it would mean 2 extended partitions.

---

### Post by flabdablet on 2010-01-22
*My sda6 (/home) is a primary partition.*

I don't believe that this statement could possibly be correct.

DOS-style partition tables (which are easily the most common kind in IBM-descended PCs, and the only ones that XP knows anything about) only have room for **four** primary partitions. Linux numbers these /dev/sdX1 through /dev/sdX4.

Because four partitions is often not enough, DOS-style partitioning allows any one of the four to be an extended partition. An extended partition contains *its own* partition table, **one** entry of which can itself be an extended partition; other entries (there's usually only one) create so-called *logical partitions* for the underlying drive. Linux numbers these from /dev/sdX5 on up, even if /dev/sdX4 doesn't exist.

So if you know for sure that your /home filesystem used to be on /dev/sda6, then you know for sure that it was on a logical partition.

Also, when cfdisk creates logical partitions, it will in fact expand any extended partitions that these are part of in order to make them fit. You don't need to create or manipulate extended partitions by hand, and should not attempt to try. Simply create a logical partition in the free space at the end of your drive. You should find that it gets named /dev/sda6, that it contains your missing /home filesystem, and that the next time you examine your drive with fdisk -l, /dev/sda3 has got bigger.

That pissy little chunk of free space right after /dev/sda2 is most likely a side effect from the Windows Setup partitioner, and best ignored.

---

### Post by meierfra. on 2010-01-22
> Won't create parition, says it would mean 2 extended partitions.
sda4 is inbetween /dev/sda5 and the free space.    You cannot have a a primary partition sitting inside an extended partition.  So cfdisk refuses to create a new partition.

> 
/home partition (/dev/sdaX, cannot remember what X was) 
My sda6 (/home) is a primary partition. 
Maybe your current /dev/sda4 used to /dev/sda6 and your home partition was /dev/sda4.

Since we do not know the exact location of your home partition, I would not try to manually   recreate the/home partition. Instead, I recommend to use testdisk. It should  be able to detect your /home partition:

Boot from the Ubuntu Live CD.You will have to enable the universe repository: (I'm pretty sure you know how to do that, but here are the directions anyway)
System->Administration->Software Sources
Check the box in the Universe line
close
Reload

Then open a terminal and type:

```
sudo apt-get install testdisk
sudo testdisk /dev/sda
```
After starting testdisk with the above command, choose

"Proceed",
"Intel",
"Analyze",
"Quick search",
Press  "N" (if  asked if you have any partition created by Vista)
Press "Enter" to continue,
select "Deeper Search" ( which could take a while)

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let us know exactly which partitions give you a directory listing.

---

### Post by flabdablet on 2010-01-22
*sda4 is inbetween /dev/sda5 and the free space. You cannot have a a primary partition sitting inside an extended partition.*

Oh, well spotted!

In fact, according to the original fdisk -l, sda4 does in fact overlap the last few cylinders of sda3 (the extended partition). Primary partitions are absolutely not supposed to do that.

*So cfdisk refuses to create a new partition.*

Yeah. If I saw what it saw, I would too!

I concur that testdisk is the right thing to use next. The output from **sudo sfdisk --dump /dev/sda** will probably also be interesting, and it would probably be good to do **sudo sfdisk -O /tmp/ptable /dev/sda** and then copy /tmp/ptable to somewhere on your stick before you let testdisk make any changes. Check the sfdisk man page to find out why.

---

### Post by amaroKer on 2010-01-25
Hey guys sorry it took so long, I hope you're still interested.

I cannot see "deeper search" option in testdisk, but what I found is hopeful.  The ones in bold are what I made the extended partition for, so it all looks alright.  Every partition except swap has files, and are all what I expect.
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 80 GB / 74 GiB - CHS 9726 255 63
     Partition               Start        End    Size in sectors
D FAT16 >32M               0   1  1     4 254 63      80262 [DellUtility]
D HPFS - NTFS              5   0  1  1309 254 63   20964825
[B]D Linux                 1310   2  1  2027 254 63   11534544
D Linux Swap            2028   0  1  2223 254 63    3148740[/B]
D Linux                 2224   0  1  9725 254 63  120519630


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock, 61 GB / 57 GiB


--


ubuntu@ubuntu:~$ sudo sfdisk --dump /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=    80262, Id=de
/dev/sda2 : start=    80325, size= 20964825, Id= 7, bootable
/dev/sda3 : start= 21045150, size= 14683410, Id= 5
/dev/sda4 : start= 32579820, size=  3148740, Id=82
/dev/sda5 : start= 21045276, size= 11534544, Id=83


```

I remember the output of sudo fdisk -l as showing the extended partition as ```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        **1310**    10482412+   7  HPFS/NTFS
/dev/sda3            **1311        2224**     7341705    5  Extended
/dev/sda4            2029        2224     1574370   82  Linux swap / Solaris
/dev/sda5            1311        2028     5767272   83  Linux
``` and I see what the problem is now with the cylinder numbers not matching up now.  Thanks guys, I just need to know how to fix this.

---

### Post by meierfra. on 2010-01-25
```
Disk /dev/sda - 80 GB / 74 GiB - CHS 9726 255 63
     Partition               Start        End    Size in sectors
D FAT16 >32M               0   1  1     4 254 63      80262 [DellUtility]
D HPFS - NTFS              5   0  1  1309 254 63   20964825
D Linux                 1310   2  1  2027 254 63   11534544
D Linux Swap            2028   0  1  2223 254 63    3148740
D Linux                 2224   0  1  9725 254 63  120519630
```

I agree, that looks good.  To write  the new partition table select each of the lines (via the up and down arrow) and then use  the right arrow key  to change the entry  in the first column so that it looks like:

```
Disk /dev/sda - 80 GB / 74 GiB - CHS 9726 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]P[/COLOR] FAT16 >32M               0   1  1     4 254 63      80262 [DellUtility]
[COLOR="Red"]*[/COLOR] HPFS - NTFS              5   0  1  1309 254 63   20964825
[COLOR="Red"]L[/COLOR] Linux                 1310   2  1  2027 254 63   11534544
[COLOR="Red"]L[/COLOR] Linux Swap            2028   0  1  2223 254 63    3148740
[COLOR="Red"]P[/COLOR] Linux                 2224   0  1  9725 254 63  120519630

```

Then press "enter". At the next screen choose "write". Press "y" if asked for confirmation and press "q" a few times to quite testdisk.

---

### Post by amaroKer on 2010-01-25
Oop, found deeper search and```
Disk /dev/sda - 80 GB / 74 GiB - CHS 9726 255 63

The harddisk (80 GB / 74 GiB) seems too small! (< 80 GB / 74 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                 2232   0  1  9733 254 57  120519624
  Linux                 2233   1  1  9735   0 57  120519624

```That's bad?

---

### Post by amaroKer on 2010-01-25
This is the best I can do, and I can always resize the Extended partion and put a new swap in there eh?```
Disk /dev/sda - 80 GB / 74 GiB - CHS 9726 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     4 254 63      80262 [DellUtility]
P HPFS - NTFS              5   0  1  1309 254 63   20964825
L Linux                 1310   2  1  2027 254 63   11534544
D Linux Swap            1963   0  1  2223 254 63    4192965
D Linux Swap            2028   0  1  2223 254 63    3148740
P Linux                 2224   0  1  9725 254 63  120519630

```Note the new Swap that showed up after deeper search.

---

### Post by meierfra. on 2010-01-25
The deep search just found some old partition.  Don't worry about that. Just do the quick search again and follow the instruction from my previous post.

---

### Post by amaroKer on 2010-01-26
Excellent.  Did that.  I was left with no swap file, but I just made a new one using gparted.  I'm glad that I didn't have to install XP again, that takes about half a day of work to get it set up to a usable condition.  Thanks a lot for your help.  Now to figure out how to mark as solved...

---

