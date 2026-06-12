---
title: "How do I find out md5sum of a disc I burnt?"
date: 2009-07-20
forum: General Help
---

### Post by s3a on 2009-07-20
I read that md5sum /dev/*something* would tell me the md5sum of my disc. What I read had *hdc* instead of the word *something*.

_My question is:_
How do I find out what to replace the word *something* with?

For example, if we were dealing with hard drives, I'd do: *sudo fdisk -l* to figure out the name of the hard drive however, I have no idea how to do this when dealing with cdrom drives. Can someone please tell me how to do this?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by prshah on 2009-07-20
> **s3a said:**
> I read that md5sum /dev/*something* would tell me the md5sum of my disc. What I read had *hdc* instead of the word *something*.

How do I find out what to replace the word *something* with?


cdroms in ubuntu typically are /dev/scd (scd0, scd1 if you have more than one cdrom drive) and are also (soft) linked to /dev/cdrom (cdrom0, cdrom1, etc).

However, md5'ing will require the media to be mounted and readable, so you would be better off using /media/cdrom (cdrom0, cdrom1, etc).

Note that no matter what you use: /dev/scd0, /dev/cdrom0, /media/cdrom0, the md5sum should come to the same.

---

### Post by rbc on 2009-07-20
First, look in the /etc/fstab file and see if the cdroms are listed there. If not, let the CD automount, then go to terminal and type:
mount

It should be the last device listed. Or, after it automounts, look at the /etc/mtab file. Again, it should be the last device listed. In my case, it is /dev/sr0. A CD-R is a bit different, in that it takes a bit more work to write to it, and one cannot delete files from it, but anything else, I would highly suggest unmounting before you run the md5 hash, since you would not want to change anything while the hash is running(sha1 or md5)
So, go to terminal and type:
sudo md5sum /dev/sr0 (or however else you cdrom is listed)
 I assume you need sudo because root owns everything under /dev.

---

