---
title: "Mounting windows 7 spanned disk in ubuntu"
date: 2010-05-01
forum: General Help
---

### Post by firesarter2 on 2010-05-01
Does anyone know how to mount a spanned ntfs volume in ubuntu? I have a partition spanned across 5 drives.  From the documentation it looks like it should be possible but I cant figure it out.  I have ubuntu 9.4 but I will change to what ever version it will work on.  The five 1500gb drive below are the ones I want to use. I tried to use ldminfo but I get the below error. 

> veli@aaaa:~/Desktop/linux-ldm-0.0.8/test$ sudo ./ldminfo /dev/sdb
lseek to -698721449472 failed
ldm_validate_privheads(): Disk read failed.
lseek to -698722399232 failed
ldm_validate_tocblocks(): Disk read failed.
Something went wrong, skipping device '/dev/sdb'
veli@aaaa:~/Desktop/linux-ldm-0.0.8/test$ sudo ./ldminfo /dev/sdb1
Something went wrong, skipping device '/dev/sdb1'


Before anyone asks I dont have the space to copy the date off to and I want to use the disk on a machine that dual boots. 

Thank you in advance. 
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e310

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37784   303499948+  83  Linux
/dev/sda2           37785       38913     9068692+   5  Extended
/dev/sda5           37785       38913     9068661   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bc0bae5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182402  1465137523   42  SFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182402  1465138583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182402  1465138583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      182402  1465138583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      182402  1465138583+  ee  GPT


---

### Post by firesarter2 on 2010-05-02
any please?

---

### Post by SnickerSnack on 2010-05-02
This page [http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1272833628689+28353475&threadId=1361776](http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1272833628689+28353475&threadId=1361776) has some information.  A post near the beginning names some software you can buy to do that, and a post near the end say that there is no free software that can do that.

---

### Post by firesarter2 on 2010-05-02
Oddly in the link that guys says he can do it in ubuntu I think it can be done. Other wise I have to stay with windows 7 or get enough hard drive space to move my data too.

---

### Post by tecnecio on 2010-05-04
Folks, I'm also interested in the subject. I have two 320gb hdd spanned into one big NTFS partition on windows 7 and  don't want to change that and be able to access/write on windows 7 and on ubuntu on the same machine.

I was gathering information over the internet and found this:

[http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt#229](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt#229)

It explain in a tecnical way how to work with software raid with the linux ntfs driver.

Hope it helps a little...
I'm still searching for answers.

---

### Post by tecnecio on 2010-05-04
Related threads:

[http://ubuntuforums.org/showthread.php?t=1115923&highlight=spanned+volume](http://ubuntuforums.org/showthread.php?t=1115923&highlight=spanned+volume)

[http://ubuntuforums.org/showthread.php?t=763612&highlight=spanned+volume+mount](http://ubuntuforums.org/showthread.php?t=763612&highlight=spanned+volume+mount)

Solution may be here:

[http://ubuntuforums.org/showpost.php?p=5148388&postcount=5](http://ubuntuforums.org/showpost.php?p=5148388&postcount=5)

---

