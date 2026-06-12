---
title: "unable to access other partitions on drive"
date: 2012-06-08
forum: General Help
---

### Post by Samushighwind on 2012-06-08
So I triple-boot a Mac.  I was formerly able to access my HFS+ and NTFS drives, and then I decided to try to enable read/write access for the HFS drive by disabling journaling and changing my UID on Linux to 502 to match my Mac drive.  I'm not sure if this was resultant and I can't remember everything I did... I ended up using pysdm at one point and that didn't work at all.  I ended up screwing up my NTFS drive even more and then restoring enough permission that I get the original stupid message again.  I also had access to my HFS+ drive before reboot for some reason.  I can clearly access the thing if I want to, but being able to do so without fancy antics would also be good..

At this point if I try to access either drive I get this message:

> Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda2 on /media/sda2

I feel like the answer's probably simple, I'm just not sure what to do and I'm super tired.  Any help would be so much appreciated.

edit: 12.04, if it matters..

---

### Post by dino99 on 2012-06-08
that is a long complex tweak, so resolving might be complex too. Did you get some usefull errors/warnings logged to help you ?

try to reconfigure:

sudo dpkg-reconfigure -phigh -a
(dont stop it, it can take a while)

---

### Post by Samushighwind on 2012-06-08
Can you explain what that does before I do it?

Also this is the thread I followed to enable write access.. I only paid any attention to the section headed "making your mac and linux home folders play nicely with one another"

[http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

---

### Post by Samushighwind on 2012-06-09
I used mountmanager to allow both drives to be mounted not just by "administrator" but by "everybody" (note that since I am an administrator, this should have been working, and I was able to mount it before..).

So my HFS+ drive mounts now with that setting.  But now with my NTFS drive I get this error:

> **Unable to mount BOOTCAMP**

Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://tuxera.com/community/ntfs-3g-faq/#unprivileged](http://tuxera.com/community/ntfs-3g-faq/#unprivileged)

I went to that link and couldn't figure out what's wrong.  Any idea?

Ben

---

