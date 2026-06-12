---
title: "Boot up - fsck message"
date: 2009-07-28
forum: General Help
---

### Post by oaxacamatt1 on 2009-07-28
Hi all,
I have something odd occuring when I boot up.  I installed 9.04 on my Toshiba laptop and then tried to put Windows 7 on.  The skinny is I aborted the windows install but when I booted Ubuntu again I got a funny message.  During the boot up it drops into text mode and the message is:

Fsck died with Exit Status 8
Filesystem failed
see var/log/fsck/checkfs if that location is writable
Please repair manually or CTRL D to continue.

And then in checkfs:
----------------
Log of fsck -C -R -A -a 
Tue Jul 28 09:30:31 2009

fsck 1.41.4 (27-Jan-2009)
fsck.ext4: Unable to resolve 'UUID=3e6ba374-83cf-4481-9c19-c79647447e86'

fsck died with exit status 8

Tue Jul 28 09:30:31 2009
----------------
Anyone?
Cheers,
M

---

### Post by philinux on 2009-07-28
I reckon all you need to do is this.

```
sudo blkid
```
 

and then fix /etc/fstab 

With the info you get from blkid

---

### Post by oaxacamatt1 on 2009-07-28
Thanks Phil,
Works great!

Issue Solved.

Cheers,
M

---

### Post by hbost on 2009-08-01
I have same issue and have tried the solutions on this forum and not much success. I have fixed GRUB (both with tty and GUI from live CD) and have updated Ubuntu packages with apt-get.

I have two 750G Seagate drives running raid 1 on an old Dell Optiplex. All was fine until I rewired my house and the Dell sat idle for 2 months.

On reboot, I get the same FSCK.ext3 died with error status 8 message.

When I run blkid, I get ID numbers for sda1, sda2, sda3 and md0. However, when i try to edit /etc/fstab, the only ID numbers are md0, md1, md2, etc.

Clearly, I have a partition and/or GRUB problem, but not savvy enough to figure it out.

One data point that may be material is that I originally had an Ubuntu 8.04 LTS install and was using PC as a desktop. I bought a new PC and moved the Dell to a file server and installed Xubuntu to save resources. When it worked, it was the cheapest, fastest file server around. However, I think this double install has screwed up GRUB.

I guess I could do a full new Ubuntu install, but I am very nervous about my files (pictures and songs) and settings and worried that I may overwrite them.

Any help appreciated.

---

### Post by Post Monkeh on 2009-08-01
so did the dell ever work after you installed xubuntu?

sounds like your fstab is screwed, there should be entries in there for all your mount points.

my file system has partitions for root, home, and 3 swap partitions.  my fstab looks like

```

proc            /proc           proc    defaults        0       0
UUID=5f2d80d5-3e99-4d13-900b-1bd81de2688d /               ext4    relatime,errors=remount-ro 0       1
UUID=d85c550a-4df4-44b3-822b-22440d4ced7e /home           ext3    relatime        0       2
UUID=7e15589a-b426-4c97-b1ba-ed68a5913b5f none            swap    sw              0       0
UUID=09806e27-3a9e-4489-b4ab-42dbc8e3dbf6 none            swap    sw              0       0
UUID=7294dc46-ff3c-4bd4-86a5-76df06044730 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

yours should look similar, there should definitely be an entry for "/", which is your main filesystem, and likely some entries for swap partitions.

i'm no expert so i don't think i can help, but by the sounds of it it should be pretty easy to fix.

---

### Post by hbost on 2009-08-01
Thanks for the quick reply, Post Monkeh.

Yes, Xubuntu ran fine for nearly 6 months before this issue.  Unfortunately, I think the Dell was shut down improperly several times by my contractor as it is set to boot when power supply turned on.  

fstab looks something like this (I am paraphrasing to keep it short}:

===========
# /dev/md0 
UUID:[numbers and letters] /ext3 relatime errors = remount -ro 0 1

# dev/md1 
UUID: [numbers and letters] /home ext3 suid,dev, relatime exec 0 2

# /dev/md2 
UUID: [numbers and letters] none swap s w

/dev/scd0 [CDROM]
============

Other tests run:

1)   cat /proc/mdstat -- md0 shows up at 12G active raid, but md1 and md2 are inactive.

2) mdadm -- shows that md0 is ok, but md1 and md2 are inactive

3) blkid -- I get the md0 UUID (which matches fstab), but then I get sda1, sda2, sda3 UUID.  No md1 or md2 UUID. 

4) I double checked my original error (which I still get) and it does have an UUID error.  That UUID does NOT match anything in fstab.

Finally, and I think this may be the issue:

5)  fdisk -l -- /dev/sda1, /dev/sda2 and /dev/sda3 are listed and look like my boot, swap and .ext3 drives (under a detectable raid) 

however, at the very bottom, I get the message "Disk /dev/md0 does not contain a valid partition table"

Unfortunately, I don't know the difference between md0 and sda1, but that appears to be the problem.  I know it is a partition issue and would be fine with going through full install/repartition with live CD if I knew my data was safe.

Thanks.

---

### Post by hbost on 2009-08-01
I hope that the problem is solved.

After chasing my tail for two days, I grabbed the original Xubuntu SERVER (I didnt realize it was the SERVER version) disk, booted it up, selected "rescue broken system", went through a couple of setup screens and simply re-installed GRUB.  No partition issues, no FSCK issues, booted right up.

I guess it helps to understand exactly what you have loaded on your system!!  I also should have known that I was using the incorrect LiveCD as the other CDs did not have the "rescue broken system" option...

Thanks for help.

H

---

### Post by Post Monkeh on 2009-08-02
glad you got it sorted, whatever was causing it.

---

### Post by hbost on 2009-08-16
Sorry for late reply and thanks for the help.

I think it was a corrupt GRUB loader/file that I fixed with Xubuntu Server LiveCD.  Went to "Fix a broken system" on the menu options and skipped everything except "Install GRUB."

Works like a charm, now.  

I think it must have shut down wrong.

Thanks again.

---

