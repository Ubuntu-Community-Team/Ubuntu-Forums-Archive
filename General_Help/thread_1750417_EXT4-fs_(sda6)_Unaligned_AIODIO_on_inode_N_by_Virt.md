---
title: "EXT4-fs (sda6): Unaligned AIO/DIO on inode N by VirtualBox; performance will be poor"
date: 2011-05-05
forum: General Help
---

### Post by imbjr on 2011-05-05
Well I've seen the source code that produces this log entry, but I'm none the wiser as to whether or not this is a problem that needs addressing, or how.

Anyone have any information on this?

---

### Post by srs5694 on 2011-05-05
I've *not* looked at the source code, but my hunch is it's related to [issues of sector alignment on Advanced Format drives,](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) RAID arrays, and SSDs. On such disks, if the data structures in the virtual disk don't align properly to the underlying physical sectors (or other data structures, such as RAID stripes), then performance can suffer.

I'm afraid I've not investigated this issue with respect to virtual disks in any detail, though, and I don't have specific suggestions for how to fix or work around the problem. AFAIK, though, it's only likely to be a problem on one of the devices that's susceptible to the issue in the first place, so depending on your disk hardware, it might be a non-issue. If you're not sure about your disk hardware on this score, please post back with details of what you've got.

---

### Post by imbjr on 2011-05-06
> **srs5694 said:**
> I've *not* looked at the source code, but my hunch is it's related to [issues of sector alignment on Advanced Format drives,](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) RAID arrays, and SSDs. On such disks, if the data structures in the virtual disk don't align properly to the underlying physical sectors (or other data structures, such as RAID stripes), then performance can suffer.

I'm afraid I've not investigated this issue with respect to virtual disks in any detail, though, and I don't have specific suggestions for how to fix or work around the problem. AFAIK, though, it's only likely to be a problem on one of the devices that's susceptible to the issue in the first place, so depending on your disk hardware, it might be a non-issue. If you're not sure about your disk hardware on this score, please post back with details of what you've got.

I have an ext4 partition (on a SATA HD) containing two VirtualBox drives formatted to NTFS. The log warning seems to imply that I'm getting sub-optimal performance when those "drives" are being written to because of the underlying ext4 partition. So far, I've not noticed any real drop in performance, but if I start to (I've only had Natty installed for a week), then I may have to change the ext4 to an ext3 partition - with the possibility of first attempting to mount the ext4 partition as ext3 instead, which I believe is possible.

---

### Post by imbjr on 2011-05-06
Here's some extra data:

> 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000adaa6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568833    5  Extended
/dev/sda5               1         523     4194304   82  Linux swap / Solaris
/dev/sda6             523        5092    36700160   83  Linux
/dev/sda7            5092       38914   271672320   83  Linux


Note: 
. There's an unallocated section before /dev/sda1 of 2Mb in size.
. sda6 and sda7 are formatted to ext4.

---

### Post by chipper_farley on 2011-05-06
I have the same issue with a RHEL VM.  I've cloned the virtual HD and am running off a different image that when the error started appearing but it still occurs.  Now I see it happen sometimes, but not all the time, when I start up the RHEL VM.  I'm stumped.

---

### Post by srs5694 on 2011-05-06
> **imbjr said:**
> I have an ext4 partition (on a SATA HD) containing two VirtualBox drives formatted to NTFS. The log warning seems to imply that I'm getting sub-optimal performance when those "drives" are being written to because of the underlying ext4 partition.

That's not my interpretation -- but I didn't write the code in question, either. I certainly know of no reason why ext4fs would produce worse results than ext3fs in this sort of situation.

Your fdisk output is uninformative. Even when dealing with conventional alignment issues on real hard disks, you need sector-precise values, not the much sloppier cylinder values produced by "fdisk -l". Please read the article in the link in my first post. In a virtual disk, you've also got to be concerned with how the virtual disk lays out its data, and that's something I don't know much about.

---

### Post by imbjr on 2011-05-06
> **srs5694 said:**
> That's not my interpretation -- but I didn't write the code in question, either. I certainly know of no reason why ext4fs would produce worse results than ext3fs in this sort of situation.

Your fdisk output is uninformative. Even when dealing with conventional alignment issues on real hard disks, you need sector-precise values, not the much sloppier cylinder values produced by "fdisk -l". Please read the article in the link in my first post. In a virtual disk, you've also got to be concerned with how the virtual disk lays out its data, and that's something I don't know much about.

Well according the data sheet for my WD3200KS-75P disk, there are 512 bytes per sector, as per the fdisk info above.

---

### Post by srs5694 on 2011-05-07
In that case, you shouldn't worry about it, at least not if my interpretation of the message is correct. If there are alignment issues within a filesystem that are unrelated to the logical vs. physical sector size issues, RAID issues, or SSD issues, then there may be something to worry about.

You might try digging into the VirtualBox documentation or even contact a developer about it if you want to be 100% sure.

---

### Post by imbjr on 2011-05-07
> **srs5694 said:**
> In that case, you shouldn't worry about it, at least not if my interpretation of the message is correct. If there are alignment issues within a filesystem that are unrelated to the logical vs. physical sector size issues, RAID issues, or SSD issues, then there may be something to worry about.

You might try digging into the VirtualBox documentation or even contact a developer about it if you want to be 100% sure.

I checked their forums and no-one has mentioned it, yet!

I think I will let this lie for now. I've not noticed any real performance hit when running my Windows 7 guest.

---

### Post by 3L33T on 2011-07-21
I'd like to bump up this thread as it has been idle for a while.

on Ubuntu 11.4, same error message, windows7 guest o/s, on hp ml150G6 server.

I have not noticed any performance hits on my windows7 guest.

IF anyone has any updates re: this issue (Re: EXT4-fs (sda6): Unaligned AIO/DIO on inode N by VirtualBox;performance will be....) please post here.

TIA!

---

### Post by euroford on 2011-07-31
The same problem, [https://bugzilla.kernel.org/show_bug.cgi?id=36722](https://bugzilla.kernel.org/show_bug.cgi?id=36722)
bug in ext4 filesystem, not solved yet.

---

### Post by MiG82au on 2011-08-05
euroford, did actually you read the bug report? It's unrelated.

---

### Post by masuch on 2011-11-12
I have came across this error as well: 
EXT4-fs (sdcX): Unaligned AIO/DIO on inode NNN by VirtualBox; performance will be poor.
But I did not notice any performance degradation.

---

### Post by fbcyborg on 2012-02-26
Hi!

I had the same problem after moving my VDI directory to an external USB 3.0 hard drive with ext4 fs.
Actually, I've noticed low speed with my virtual machines. Do you think it would be better to use XFS instead?

---

### Post by mariposil on 2012-05-11
bad news:

[http://askubuntu.com/questions/118140/unaligned-aio-dio](http://askubuntu.com/questions/118140/unaligned-aio-dio)

---

### Post by imbjr on 2012-05-11
> **mariposil said:**
> bad news:

[http://askubuntu.com/questions/118140/unaligned-aio-dio](http://askubuntu.com/questions/118140/unaligned-aio-dio)

I'm still getting this in my logs and I've never seen any real issue with it. Glad to know it's not something more critical.

---

### Post by SteveONCSU on 2012-07-20
I'm seeing this same problem.  So how do you realign the VDI hard disk?  I don't notice any performance problem but I would like to get rid of this message.

---

### Post by drbin on 2012-08-01
have the same on raid-1 sata disks Dell server.
could it be the host  i/o option under the drives selection tab?
I usually prefer to uncheck.

---

### Post by karlmikaze on 2012-10-18
For what it's worth, here's my further findings on this topic.

I stumbled upon an IBM devworks article dated 04/2010 that includes some benchmarks and impact scenarios using different filesystems:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/")

The essence, as I understood it:
[LIST]
[*]if you're seeing this error on Advanced Format type drives (newer, bigger HDs, using default 4k blocksize), the speed penalty is substantial. You should rethink your partitioning layout and probably move away from 512k block size in linux.
[*]If you're (like me) on a HW RAID5 of bigger, newer disks and seeing this error, the penalty for ext4 filesystems on top is somewhere between 5-30%.
[*]YMMV with other filesystems etc.
[/LIST]

In my use case (SATA disks in HWRAID5, lvm2 on top, ext4 fs), I decided to live with the daily warning and the (neglecable) performance hit - which I didn't notice yet in real life.

hth Chris

---

### Post by CharlesA on 2012-12-15
> **SteveONCSU said:**
> I'm seeing this same problem.  So how do you realign the VDI hard disk?  I don't notice any performance problem but I would like to get rid of this message.

I have the same thing, but only with only 1 of my VDIs. I will see if exporting it and importing it fixes it.

EDIT: It turned out the problem was that VM didn't have "Use host I/O cache" enabled. All good now. :)

---

### Post by tobias-hochguertel-p on 2013-10-04
> **CharlesA said:**
> I have the same thing, but only with only 1 of my VDIs. I will see if exporting it and importing it fixes it.

EDIT: It turned out the problem was that VM didn't have "Use host I/O cache" enabled. All good now. :)

You saved my Evening! ;-) I have had One VM Machine which had disabled this Feature. After Enabling "Use host I/O cache" all slowness were gone! THANKS!

---

