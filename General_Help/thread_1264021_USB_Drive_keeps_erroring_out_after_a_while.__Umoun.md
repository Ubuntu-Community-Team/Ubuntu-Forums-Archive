---
title: "USB Drive keeps erroring out after a while.  Umounting / mounting fixes the problem"
date: 2009-09-11
forum: General Help
---

### Post by thejipster on 2009-09-11
I have a 500 Gig USB drive that keeps disconnecting.  When I try to access the directory, I see this error message.
root@ubuntu:/videos# dir
dir: reading directory .: Input/output error


I ran fsck -c /dev/sdc1 and after 6 hours, it finished.
I ran fsck /dev/sdc1 and it said that the number of mounts have been exceeded and a standard check was performed , which also succeed.  So at this point ,I don't know what to do next.
Any ideas why this is erroring out?

Below are some messages from dmesg, /var/log/messages

Interesting, I also noticed that the drive is redetected as sdd intead of sdc occasionally.  I am not sure why this is happening.

---------------------

Dmesg shows 
[179340.670783] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
[179340.670805] Remounting filesystem read-only
[179340.671193] Buffer I/O error on device sdc1, logical block 0
[179340.671199] lost page write due to I/O error on sdc1
[179340.676349] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
[180897.791099] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0


/var/log/messages 
Sep 11 13:46:08 ubuntu kernel: [177901.911117] scsi 12:0:0:0: Direct-Access     Generic  External         1.04 PQ: 0 ANSI: 4
Sep 11 13:46:08 ubuntu kernel: [177901.914196] sd 12:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
Sep 11 13:46:08 ubuntu kernel: [177901.915575] sd 12:0:0:0: [sdd] Write Protect is off
Sep 11 13:46:08 ubuntu kernel: [177901.917367] sd 12:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
Sep 11 13:46:08 ubuntu kernel: [177901.918689] sd 12:0:0:0: [sdd] Write Protect is off
Sep 11 13:46:08 ubuntu kernel: [177901.919570]  sdd: sdd1
Sep 11 13:46:08 ubuntu kernel: [177901.927524] sd 12:0:0:0: [sdd] Attached SCSI disk
Sep 11 13:46:08 ubuntu kernel: [177901.928259] sd 12:0:0:0: Attached scsi generic sg3 type 0
Sep 11 14:01:34 ubuntu -- MARK --
Sep 11 14:10:06 ubuntu kernel: [179340.671199] lost page write due to I/O error on sdc1
Sep 11 14:21:34 ubuntu -- MARK --

---

