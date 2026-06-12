---
title: "CD/DVD drive not working"
date: 2010-12-26
forum: General Help
---

### Post by LazyBrian on 2010-12-26
I have a Dell XPS 1530 that came with Ubuntu pre-installed.  I've upgraded to the Ubuntu 10.10 and have used it without issues for months.  It has been a great laptop.  However, I recently noticed that the built-in CD/DVD drive no longer auto-mounts disks.  I can boot off the CD/DVD drive just fine, but if I boot the laptop off the hard drive and try to pop in a CD or DVD, the disk is not auto-mounted and the following error appears in the system log:

gvfsd-cca[2423]: segfault at fffffffe ip 001c2e21 sp b7660b10 error 4 in libc-2.12.1.so[152000-157000]

I also get an error dialog:  Unable to mount Audio disc:  Dbus error org.freedesktop.DBus.Error.NoReply Message did not receive a reply (timeout by messagebus)

My fstab looks like this:

/dev/scd0    /media/cdrom1 udf,iso9660 user, noauto,exec,utf8 0   0

if I try to &quot;mount /dev/scd0&quot;, I get an error &quot;wrong fs type, bad option, bad superblock on /dev/sr0 missing codepage or helper program or other error.  

Tailing dmesg shows:

UDF-fs:  No anchor found
UDF-fs:  No partitioned found (1)
[sr0] Result:  hostbyte=DID_OK driverbyte=DRIVER_SENSE
[sr0] Sense Key:  Illegal Request [current]
[sr0] Add. Sense:  Illegal mode for this track
[sr0] CDB:  Read(10):  . . . . 
end_request I/O error, dev sr0, sector 64
isofs_fill_super:  bread failed dev=sr0, iso_blknu16, block=16
gvfsd-cca[2423]: segfault at fffffffe ip 001c2e21 sp b7660b10 error 4 in libc-2.12.1.so[152000-157000]

---

### Post by dcstar on 2010-12-26
> **LazyBrian said:**
> I have a Dell XPS 1530 that came with Ubuntu pre-installed.  I've upgraded to the Ubuntu 10.10 and have used it without issues for months.  It has been a great laptop.  However, I recently noticed that the built-in CD/DVD drive no longer auto-mounts disks.  I can boot off the CD/DVD drive just fine, but if I boot the laptop off the hard drive and try to pop in a CD or DVD, the disk is not auto-mounted and the following error appears in the system log:

gvfsd-cca[2423]: segfault at fffffffe ip 001c2e21 sp b7660b10 error 4 in libc-2.12.1.so[152000-157000]

I also get an error dialog:  Unable to mount Audio disc:  Dbus error org.freedesktop.DBus.Error.NoReply Message did not receive a reply (timeout by messagebus)

My fstab looks like this:

/dev/scd0    /media/cdrom1 udf,iso9660 user, noauto,exec,utf8 0   0
..........

There should be **no** fstab entry for CD/DVDs from 10.04 onwards - comment it out as it is a "leftover" from older versions.

---

### Post by LazyBrian on 2010-12-30
Thanks, that seemed to fix it.

---

