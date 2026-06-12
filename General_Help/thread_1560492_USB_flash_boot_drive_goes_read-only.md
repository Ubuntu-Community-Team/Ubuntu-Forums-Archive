---
title: "USB flash boot drive goes read-only"
date: 2010-08-24
forum: General Help
---

### Post by blacks on 2010-08-24
I have a linux server running ubuntu 10.04, kernel Linux server 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux.  A few months ago I installed ubuntu to a USB flash drive (Patriot 16GB) and was able to successfully boot off it, and everything was running fine.  Then all of a sudden I noticed that the root filesystem was read-only, and I saw errors in the kernel log:
[  725.528732] sd 2:0:0:0: [sdc] Unhandled sense code
[  725.528742] sd 2:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  725.528750] sd 2:0:0:0: [sdc] Sense Key : Medium Error [current] 
[  725.528759] sd 2:0:0:0: [sdc] Add. Sense: Unrecovered read error
[  725.528768] sd 2:0:0:0: [sdc] CDB: Read(10): 28 00 00 1e 00 cc 00 00 d0 00

I tried reading the drive to see if there was a problem with the drive itself:
root@server:~# dd if=/dev/sdc of=/dev/null 
dd: reading `/dev/sdc': Input/output error
1966184+0 records in
1966184+0 records out
1006686208 bytes (1.0 GB) copied, 2.12427 s, 474 MB/s


But the strange thing is that if I put that usb stick in a different linux server, I'm able to read the whole drive.  If I run fsck, it fixes a bunch of errors, but when I put the drive back in the original PC it will work for a while and then fail with the same type of I/O error (not at the same offset though).

I had this same problem occur on a different USB stick in the same server, I had thought it was bad media so I replaced it, but now the same problem is happening on a different usb drive.  I have backups of the data, but I would really like to figure out what is causing this before I throw in the towel and buy a new PC.

If it helps, it looks like [http://superuser.com/questions/158751/ubuntu-usb-flash-boot-drive-gets-spontaneous-unhandled-sense-code-error-and-cau](http://superuser.com/questions/158751/ubuntu-usb-flash-boot-drive-gets-spontaneous-unhandled-sense-code-error-and-cau) is a report of a different user having the same problem.

Any suggestions on how to further diagnose this problem?

---

### Post by ellgor on 2010-08-25
Hi, 

I was having similiar issues with a pendrive, found a post that said that an app called "usbmount" was the culprit, I removed it, problem solved.

Regards, Ellgor.

---

### Post by blacks on 2010-08-26
> **ellgor said:**
> Hi, 

I was having similiar issues with a pendrive, found a post that said that an app called "usbmount" was the culprit, I removed it, problem solved.

Regards, Ellgor.

I checked and I do not have that package installed.

---

