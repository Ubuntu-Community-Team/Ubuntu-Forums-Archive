---
title: "deleted 2 partitions with gparted now will not boot, more within pls and thx"
date: 2012-08-26
forum: General Help
---

### Post by MaN227 on 2012-08-26
hello all,
well , I made a real bonehead move today. I had pc set up to boot Mint, Ubuntu and win7. Ubuntu and Win7 on a SSD and Mint on seperate 1 TB HD , I also have a 2TB storage drive. 

referencing the boot choices provided by grub I wanted to delete the Mint partitions (mint 11 and mint 12 each on their own partition)  
mint 11 on /dev/sdb5 and mint 12 on /dev/sdb7

for reference my win7/ubuntu ssd is dev/sda1 <the ssd. ubuntu installed along windows. i.e.  in grub I would choose the win7 loader and arrow down to ubuntu to boot it. 

here is what I did:
in ubuntu I opened gparted and selected the 2 aforementioned mint partitions and deleted them, one then reboot (sdb5), no worries, then second (sdb7) and reboot and ... then nothing. totally bummed now to say the least, as it took me quite some time to get win7 and ubuntu 12.04 LTS just how I wanted them. 

I am not even sure this can be fixed or not, but before starting over from scratch and reformatting the disk I figured I would ask here in hopes of finding a solution to recover from my idiotic move. 

from what I have gathered so far (info wise) I will assume you need to see this info from the terminal for starters. 

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbec7f397

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   234438655   117218304    7  HPFS/NTFS/exFAT

[COLOR=Red][B]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   567952002   283872577+   7  HPFS/NTFS/exFAT
/dev/sdb3       567955454  1933662207   682853377    f  W95 Ext'd (LBA)
/dev/sdb4      1933663725  1953520064     9928170    7  HPFS/NTFS/exFAT
/dev/sdb5      1916889088  1933662207     8386560   82  Linux swap / Solaris[/B][/COLOR]

Disk /dev/sdg: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f408a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  3907024895  1953511424    7  HPFS/NTFS/exFATany and all guided assistance, I assure you, is GREATLY GREATLY APPRECIATED. 

did I bite the big one, or is there hope? I will stand by watching for a reply. 

when I reboot it says Grub Rescue and that is it.

EDIT: I should note being able to boot win7 and Ubuntu from the SSD is more important to me than any data loss, partition recovery from the HDD in question.

---

### Post by spiky001 on 2012-08-26
Hi  The only linux partition I can see is /dev/sdb5 1916889088 1933662207 8386560 82 Linux swap / Solaris which is a swap partition. Do you have a 12.04 disc you can boot. Do you know which partition you installed ubuntu on??

---

### Post by Rexilion on 2012-08-26
> **spiky001 said:**
> Hi  The only linux partition I can see is /dev/sdb5 1916889088 1933662207 8386560 82 Linux swap / Solaris which is a swap partition. Do you have a 12.04 disc you can boot. Do you know which partition you installed ubuntu on??

Ubuntu is installed on /dev/sda1 alongside Windows 7. Could it be possible that you installed the bootloader to /dev/sdb5 and did not notice that?

Maybe the MBR was placed there?

Anyways, doesn't matter *that much*. If all is well, you can still boot /dev/sda1 with Grub :) .

---

### Post by MaN227 on 2012-08-26
thank you for the replies fellaz , much appreciate them ;)

luckily I had the ubuntu 12.04 beta on cd lying around, I ran the live cd and after seeing this forum I did a bit more searching and found this link [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

boot-repair was easy enough to download and install, ran it and after just a short while it says boot grub has been fixed.  I was quite shocked that without any other input from me, that it could correct my mistakes. 

so I removed the live cd and rebooted. and the grub loader appeared now showing win7 & ubuntu & memtest . being that I deleted the partitions that had mint on them they no longer showed on the main grub loader screen. 

when I choose ubuntu from the choices now given, it asks if I want to boot the latest kernel install or older versions of mint. 

so as i'm VERY happy that boot-repair fixed the grub loader and removed the old kernel entries from the initial load screen., the old kernel entries are still showing in the ubuntu boot menu. not sure if this makes sense the way i word it or not. 

now I'm left with 2 questions:
1.  how would I go about being able to use the un-partitioned space left from deleting the Mint partitions? to be honest as I hosed things up already , I'm afraid to make another stupid mistake and make something else not work. 

     I have about 644 Gig's unallocated at this point and would like to be able to reclaim that space for use. the only option Gparted shows to me is click new> create as Logical Partition. I'm also unsure of the file system I should choose for it, being that I have man windows games and apps installed on this hdd so as not to use up my precious SSD space, I assume choose a file system of NTFS? 


2. is it possible to remove the entries not needed in the unbuntu boot menu page?

I hope that someone can help me with this issues and I also help the link I provided can help another user that makes a bone head move such as mine to at least be able to boot the OS's they have installed, it simply could not have been easier than using  boot-repair.

---

### Post by Rexilion on 2012-08-26
> **MaN227 said:**
> thank you for the replies fellaz , much appreciate them ;)

No problem, glad we could help in some way.

> **MaN227 said:**
> 1.  how would I go about being able to use the un-partitioned space left from deleting the Mint partitions? to be honest as I hosed things up already , I'm afraid to make another stupid mistake and make something else not work. 

     I have about 644 Gig's unallocated at this point and would like to be able to reclaim that space for use. the only option Gparted shows to me is click new> create as Logical Partition. I'm also unsure of the file system I should choose for it, being that I have man windows games and apps installed on this hdd so as not to use up my precious SSD space, I assume choose a file system of NTFS? 

I took a closer look at your partition table, seems a bit insane to me:

> /dev/sdb3 567955454 1933662207 682853377 f W95 Ext'd (LBA)
/dev/sdb4 1933663725 1953520064 9928170 7 HPFS/NTFS/exFAT
/dev/sdb5 1916889088 1933662207 8386560 82 Linux swap / Solaris

If you look at the sector counts, then /dev/sdb3 is a logical partition. This a partition which can hold another 4 (I'm not sure) primary partitions (within the logical partition). This is because the MBR is designed to only hold a maximum of 4 partitions. So with logical partitions, you can extend this maximum. However, looking at your partition table you posted first. I see some stuff. You should btw post a new partition table, since you changed it again right? (i.e. removed /dev/sdb5).

If you look at the sectors, then I conclude:

- /dev/sdb3 is a logical partition which holds /dev/sdb5 at the end(!)
- /dev/sdb4 is beyond the logical partition /dev/sdb3(!)

The sequence doesn't make much sense. But now I assume you deleted /dev/sdb3,4 and 5. You can create one big partition which can be primary since that would be number 3.

If you want to create a filesystem that works good on both Linux and Windows, you should go for NTFS. VFAT is also an option but has an 4GiG limit on each file.

Make sure you use the fuse filesystem ntfs-3g to access this partition. Not the ntfs driver from the kernel.


> **MaN227 said:**
> 2. is it possible to remove the entries not needed in the unbuntu boot menu page?

I hope that someone can help me with this issues and I also help the link I provided can help another user that makes a bone head move such as mine to at least be able to boot the OS's they have installed, it simply could not have been easier than using  boot-repair.

Yes, these stale entries are now in your grub.cfg and (maybe) in your /etc/default/grub. /etc/default/grub is user configuration, so it will overwrite grub.cfg. You have to look for those files and post their contents here. They might even be placed somewhere else by Mint (don't have a clue right now).

---

### Post by oldfred on 2012-08-26
Is Ubuntu really a wubi install inside the Windows? And then the swap is just from the other installs you deleted?

Post the linkd from a full BootInfo report from Boot-Repair.

---

### Post by MaN227 on 2012-08-27
here is the requested info from fdisk as it is today
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbec7f397

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   234438655   117218304    7  HPFS/NTFS/exFAT

[COLOR=Blue]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   567952002   283872577+   7  HPFS/NTFS/exFAT
/dev/sdb3       567955454  1933662207   682853377    f  W95 Ext'd (LBA)
/dev/sdb4      1933663725  1953520064     9928170    7  HPFS/NTFS/exFAT
/dev/sdb5      1916889088  1933662207     8386560   82  Linux swap / Solaris[/COLOR]

Disk /dev/sdg: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f408a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  3907024895  1953511424    7  HPFS/NTFS/exFAT

as to this: > **Rexilion said:**
> Make sure you use the fuse filesystem ntfs-3g  to access this partition. Not the ntfs driver from the kernel. 
sorry I do not follow, not familiar with the terms, rather noobish with regards to many things, sadly.

---

### Post by Rexilion on 2012-08-27
> **MaN227 said:**
> here is the requested info from fdisk as it is today

That means what I said in my previous post applies.

> **MaN227 said:**
> as to this:  
sorry I do not follow, not familiar with the terms, rather noobish with regards to many things, sadly.

Gheh, some people call this 'choice'. However, Linux sometimes multiple ways to do the same thing which goes directly against the Unix philosophy.

The thing is, the kernel NTFS driver is not mature when it comes to writing. It's only used if you install another OS alongside Windows. This driver can only write if original and modified filesize stay the same!

The ntfs-3g is a FUSE module (FUSE is in the kernel) that allows you to do things from userspace instead of kernelspace (except for a little help).

Basically, they are two different drivers which are doing somewhat the same thing. ntfs-3g can be installed as a software package and you are ready to go.

---

### Post by MaN227 on 2012-08-27
> **oldfred said:**
> Is Ubuntu really a wubi install inside the Windows? And then the swap is just from the other installs you deleted?

Post the linkd from a full BootInfo report from Boot-Repair.

a bit of history, may clear some things up. I started off with the 1TB drive with a win install. partitioned the drive with a second win install. after first install went wonky I deleted its partition and reformatted to NTFS and used it as storage space. 

next I took an interest in Linux and installed Mint 11 and then Mint 12 on the 1TB drive. at this point grub took over boot loading and mint was the default OS in the boot order. 

next I purchased a vertex 3 SSD, install win7 Ultimate, came across Ubuntu and played around with the live cd and decide to install it as well to the SSD using Wubi, as I have no grasp of grub and the fact that it took over the boot options and mint was set as first loading OS, I didn't want to risk things going haywire, so therefore Wubi seemed the easiest way to get the Ubuntu install up and running, with it being all taken care of by wubi, nothing at all got messed up. Mint was still the first OS in the list and the other choices were then windows on sda or sdb< the install that got hosed up. 

when I wanted to use Ubuntu I would arrow down to the first windows in list (the SSD install) choose windows and then I had option of first booting Win7 or arrow down to boot Ubuntu. 

I then determined I liked Ubuntu better for a Linux distro and not knowing for sure how to go about it I simply deleted the two partitions that housed mint 11 and mint 12 and that was yesterday when things got really hosed up for me and I posted here. 

I will assume looking back at it being that mint 12 was the default OS in grub boot order that , grub taking care of booting and the MBR was on the deleted mint 12 partition, and since it was handling the boot of the rig that is why it would no longer boot, mind you I do not know , I'm just assuming. I also assumed (lol wrongly ) that there would be no problem deleting the mint partiton's and would still be able to use win7 and unbuntu, I was dead wrong. 

so there you have the long and short of it. 

as far as the swap partition, I made that there on the 1 TB drive (again assuming) that it would prolong the life of my new SSD, not having so many small reads and writes being performed on the SSD. perhaps I did not do this correctly either, as using the sysmonitor screenlet it NEVER shows any percentage of the swap being used. 

I should note this is a 64 bit system

and finally here is the link to the boot-repair report 
[http://paste.ubuntu.com/1167508/](http://paste.ubuntu.com/1167508/)

and AGAIN, I cannot forget to remind you all how much I appreciate any help and/or guidance you provide. Thank God for there still being goodness in the human race, for live linux distro's and the interwebs of this world . :)

I edit to add this, I suppose it will make what is going on with the partition of the 1TB drive more clear 

click thumbnail below

[[IMG]http://img255.imageshack.us/img255/148/devsdbgparted005.th.png[/IMG]]("http://img255.imageshack.us/i/devsdbgparted005.png/")

---

