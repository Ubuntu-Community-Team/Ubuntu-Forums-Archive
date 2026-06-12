---
title: "loss data after halt command"
date: 2009-12-02
forum: General Help
---

### Post by SGWW on 2009-12-02
Hello. I nave had a big trouble and looking for good advice.

My boss has just shutded down server with halt command when very important files were in work (share resources) and certainly some critical data lost after that. Are there any way to recover lost files.

Thank you in advance

---

### Post by u.b.u.n.t.u on 2009-12-02
> **SGWW said:**
> Hello. I nave had a big trouble and looking for good advice.

My boss has just shutded down server with halt command when very important files were in work (share resources) and certainly some critical data lost after that. Are there any way to recover lost files.

Thank you in advance

Send the boss to a class of "Computers 101"!

Seriously though, your question is far too general. More details are needed such as the operating system(s) used at the time and the software.

Data on RAM can not be recovered. Data on a HDD can be recovered most times. It is essential that the computer with the affected data NOT be used. No more data written or it may overwrite the lost data.

Once you have provided some details a more precise suggestion may be given.

---

### Post by SGWW on 2009-12-02
Ok ... thank you for your post ... I try to give more information.

Operation system is ubuntu server 9.04 using as samba file server with w2k3 domain authentification.

There is raid1 software device  /dev/md4 whic consist  of 2 HDDs ... mount point for md4 is /terabyte, share with samba ...

File system is ext3fs

When server was halting people working whith /terabyte ...

I can not stop server now because it is very important for current work. Also i can show you any config file you need.

---

### Post by SGWW on 2009-12-02
May be /proc/mdstat  and fdisk -l can be usefull

```

/proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md4 : active raid1 sdc1[0]
      976759936 blocks [2/1] [U_]

md_d4 : active raid1 sdd1[1]
      976759936 blocks [2/1] [_U]

md1 : active raid1 sda2[0] sdb2[1]
      916227008 blocks [2/2] [UU]

md2 : active raid1 sda4[0] sdb4[1]
      1935744 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      58596992 blocks [2/2] [UU]

unused devices: <none>
``````
 sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00010f91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056   fd  Linux raid autodetect
/dev/sda2            7296      121360   916227112+  fd  Linux raid autodetect
/dev/sda4          121361      121601     1935832+  fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000326af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7295    58597056   fd  Linux raid autodetect
/dev/sdb2            7296      121360   916227112+  fd  Linux raid autodetect
/dev/sdb4          121361      121601     1935832+  fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60023c6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf12e07b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 60.0 GB, 60003319808 bytes
2 heads, 4 sectors/track, 14649248 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md2: 1982 MB, 1982201856 bytes
2 heads, 4 sectors/track, 483936 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 938.2 GB, 938216456192 bytes
2 heads, 4 sectors/track, 229056752 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md_d4: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md_d4 doesn't contain a valid partition table

Disk /dev/md4: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md4 doesn't contain a valid partition table


```

---

### Post by u.b.u.n.t.u on 2009-12-02
The basic theory goes something like this, files on the hard drive remain until such time as they are over written. So it becomes a matter of determining which hard drive(s) has what information and accessing that hard drive(s) through a network or external harddrive or usb.

The procedure is to use an eternal connection to start a scan for deleted files and then copy those files off the hard drive in question.

The only data that would be lost, in theory, would be the data not written on the hard drive. As most relevant software provides periodic saving, the data loss should be minimised.

I am unfamiliar with what data recovery software tools exist in the linux environment, but on the windows side of things there are many options, for example:

[http://www.piriform.com/recuva](http://www.piriform.com/recuva)


UPDATE

I see you have added another post, while I was writing this. It seems you need to find out what HDD data recovery options are available for linux. Perhaps you may wish to create a new thread here titled "Need Linux HDD Data Recovery Advise" and specifically request what software tools to use and how to use them. That would seem to be the next logical step.

In the meantime, if you can avoid writing to the hard drive(s) in question for doing such may overwrite data that you wish to recover.

---

### Post by SGWW on 2009-12-02
Thank you very much, I've been useing  R-studio software ... it has helped me ...

---

### Post by u.b.u.n.t.u on 2009-12-02
> **SGWW said:**
> Thank you very much, I've been useing  R-studio software ... it has helped me ...

Thanks for the update and all the best.

---

