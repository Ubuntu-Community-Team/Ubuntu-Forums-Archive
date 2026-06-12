---
title: "Unable to boot (/root empty??)"
date: 2010-02-11
forum: General Help
---

### Post by Deadseraph on 2010-02-11
I recently had my computer shut down thanks to lack of power (adapter came out while I wasn't watching) and when trying to re-boot, I am unable to get to the splash screen. The white ubuntu icon comes up, fades out, and the computer remains black until I ctrl+alt+del to restart. When booting in recovery mode, an interesting list of errors comes up. Evidently, it cannot fild /root/sys, /root/dev and /root/proc because there is "No such file or directory" and it cannot init because the target filesystem doesn't have "/sbin/init". When going through the filesystem, I also don't see many of my files, which leads me to believe it's booting off some random system I don't actually have files in/a filesystem that doesn't exist (is that possible?).
 
For the record, I'm running 9.10 with an xfs filesystem and kernel 2.6.31-19 primarily, but the problem persists through the other kernels I have, which leads me more to the conclusion it's not the kernel, but the fs that's not working.
 
Any help is greatly appreciated, thanks in advance!

---

### Post by Deadseraph on 2010-02-11
Upon looking through the recovery, it would appear it's just throwing up error after error, "UNC" errors repeatedly of note, and going through the same process for about 30 seconds before moving on...don't know if that's of any help though, anybody got a debugging process for solving this?

---

### Post by dearingj on 2010-02-11
I'd recommend you boot from a Live CD or USB if you can, and then use Gparted (I think the live cd calls it Partition Editor) to check your hard drive's Ubuntu partition(s) for errors.

---

### Post by Deadseraph on 2010-02-12
After downloading 9.10 again and creating a live cd, I've run all the scans I can find and it's still not booting correctly.

Is it worth Re-Installing the /boot sector?  If I delete that partition only (I have it set up on a separate ext2) then will it change the boot from the way it was before I had this problem?

Also, when going through my partitions, I noticed an option to mount a drive without formatting, should I re-mount my xfs partition without formatting it?  Will that erase my data?

Sorry for all the questions, just trying to get this worked out.

---

### Post by john newbuntu on 2010-02-12
Time for an "fsck" from a liveCD into each of your linux filesystems.

---

### Post by Deadseraph on 2010-02-12
Okay, I'm fairly new...how exactly would I go about doing that?  I can run the terminal, so I'm going to assume it's right from there, but after that I'm lost.

---

