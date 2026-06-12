---
title: "Dead disk"
date: 2010-03-16
forum: General Help
---

### Post by Boobybro on 2010-03-16
hi guys, I have a seagate external hdd which has died. Lots of personal stuff on it so need to restore. Any suggestions as to a program which can restore this disk.

---

### Post by srs5694 on 2010-03-16
That depends on what you mean by "died." Please post details of what the disk does and does not do. For instance:


[list]
[*]Check your /dev/sda? files before and after plugging in and turning on the disk. (Wait a few seconds after doing this.) Does a new device filename appear?
[*]Can you locate the disk in the output of "sudo fdisk -l" or in a GParted list?
[*]Does the disk mount at all? If so, what's preventing you from accessing your files? (Do they not appear? Do you get permissions errors? Etc.)
[*]What filesystem(s) are you using on the disk?
[/list]


Depending on the answers to these (and perhaps other) questions, somebody may be able to suggest steps to recover your data; or the answer may be "kiss your data goodbye."

---

### Post by Boobybro on 2010-03-17
> **srs5694 said:**
> That depends on what you mean by "died." Please post details of what the disk does and does not do. For instance:


[LIST]
[*]Check your /dev/sda? files before and after plugging in and turning on the disk. (Wait a few seconds after doing this.) Does a new device filename appear?
[*]Can you locate the disk in the output of "sudo fdisk -l" or in a GParted list?
[*]Does the disk mount at all? If so, what's preventing you from accessing your files? (Do they not appear? Do you get permissions errors? Etc.)
[*]What filesystem(s) are you using on the disk?
[/LIST]


Depending on the answers to these (and perhaps other) questions, somebody may be able to suggest steps to recover your data; or the answer may be "kiss your data goodbye."
The disk regesters in disk utilities but will not mount just regesters as empty . Have tried mount manager with the same result. Therefore sees the disk but will not mount it.
sudo fdisk -l gives this result :-


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcaf9cbae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150255913+  83  Linux
/dev/sda2           18707       19457     6032407+   5  Extended
/dev/sda5           18707       19457     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe02ae02a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14947   120057856    7  HPFS/NTFS

Disk /dev/sdg: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a1be21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       48640   390700768+   0  Empty

which does not include the dead disk. The file sysatem is ntfs (done before I became enlightened.
Any ideas welcome.

---

### Post by linden940 on 2010-03-17
take it apart very carfuly and the hard drive thats inside is like any other hard drive....if you have a desktop plug it in a slave *NOT AS THE MASTER DRIVE!!!! * and see if you can get into like that...sometimes the hard drive is fine...its the board inside that gets to hot and it shorts out causing it to fail and not work as it should....

i cant even start to tell u how many external harddrives i got for a few pennys becuz it was "dead" and the hard drive worked just fine...it was the small little green board inside that got to hot an stoped working.


*thats a very cheap way to get 500gb+ hdds ;) *

---

