---
title: "Help mounting external hard drive"
date: 2010-12-02
forum: General Help
---

### Post by penguinmaster on 2010-12-02
I'm having some major trouble mounting a hard drive that I pulled from an iPod.  The drive was working in the ipod when I pulled it, but I'm getting some errors when trying to mount it.  

I have completely wiped the drive and reimaged it as a ext2 file system thinking it would work.  When I plug the drive in it shows up in Nautilus, but refuses to mount.  When I try to force mount in terminal I get the following message.

```
tom@Tom-D:~$ sudo mount /dev/sdb
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
tom@Tom-D:~$ sudo mount /dev/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

My dmesg | tail then reads this.

```
tom@Tom-D:~$ dmesg | tail
[ 1292.674584] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 0d f9 4b a8 00 00 01 00
[ 1292.674592] end_request: I/O error, dev sdb, sector 234441640
[ 1414.013061] sd 4:0:0:0: [sdb] Unhandled sense code
[ 1414.013065] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1414.013069] sd 4:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1414.013079] Info fld=0x0
[ 1414.013080] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1414.013083] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 02 00 00 02 00
[ 1414.013089] end_request: I/O error, dev sdb, sector 2050
[ 1414.013094] EXT2-fs (sdb1): error: unable to read superblock

```

I then have tried to run a fsck on it to fix it. Getting this message.

```
tom@Tom-D:~$ sudo fsck /dev/sdb
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sdb: clean, 14/7331840 files, 475411/29305206 blocks
tom@Tom-D:~$ sudo fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sdb1: clean, 11/7323648 files, 474894/29289472 blocks

```

I've also tried to repair the superblock error with no avail.  

My dmesg | tail says this.

```
tom@Tom-D:~$ dmesg | tail
[ 1292.668581] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1292.668585] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 0d f9 4b a8 00 00 01 00
[ 1292.668593] end_request: I/O error, dev sdb, sector 234441640
[ 1292.674569] sd 4:0:0:0: [sdb] Unhandled sense code
[ 1292.674571] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1292.674575] sd 4:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1292.674578] Info fld=0x0
[ 1292.674580] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1292.674584] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 0d f9 4b a8 00 00 01 00
[ 1292.674592] end_request: I/O error, dev sdb, sector 234441640

```

Can anyone help me with this??

Thanks!

---

### Post by thatguruguy on 2010-12-02
From the errors you're getting, I wonder about the condition and compatibility of the hard drive controller.

---

### Post by penguinmaster on 2010-12-02
I was thinking of that as well.  Maybe I need to be looking at buying a new enclosure with a new controller.  

There cheap enough so I guess I'll give that route a shot.

Thanks!

---

### Post by penguinmaster on 2010-12-02
So I just plugged in a 4.0 gig usb flash drive, which previously worked, and now I'm getting the exact same message as above.  Not sure what that means!

---

### Post by thatguruguy on 2010-12-02
Now it sounds like a USB problem.  Have you tried re-booting?

---

### Post by penguinmaster on 2010-12-02
Yes, many times.

---

### Post by penguinmaster on 2010-12-02
Nevermind on the 4 gig flash drive. I now have that working again.

---

