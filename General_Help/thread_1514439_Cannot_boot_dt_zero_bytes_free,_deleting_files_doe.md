---
title: "Cannot boot d/t zero bytes free, deleting files does not free space"
date: 2010-06-21
forum: General Help
---

### Post by bovender on 2010-06-21
Hi all,

I have an urgent problem -- as of this morning, I can no longer boot into my Ubuntu 10.10 system.

I guess the problem is that there are allegedly 0 bytes free on that drive. However, last night there were still about 1.7 GiB free.

Deleting several large files on the drive does NOT free any space. I guess something must be wrong with the file system on the disk??

I did a fsck -f on the drive, everything is reported clean.

How can I fix the drive so that the free space is actually reported as free_

Help would be greatly appreciated. Murphy's law -- of course I have an important work deadline coming up...

Thanks

---

### Post by dim3000 on 2010-06-21
> **lazy_leukocyte said:**
> Hi all,

I have an urgent problem -- as of this morning, I can no longer boot into my Ubuntu 10.10 system.

I guess the problem is that there are allegedly 0 bytes free on that drive. However, last night there were still about 1.7 GiB free.

Deleting several large files on the drive does NOT free any space. I guess something must be wrong with the file system on the disk??

I did a fsck -f on the drive, everything is reported clean.

How can I fix the drive so that the free space is actually reported as free_

Help would be greatly appreciated. Murphy's law -- of course I have an important work deadline coming up...

Thanks

Wait a second back up, your're just teasing Murphy now, why are you using a DEVELOPMENT-BUG-PRONE-not-yet-even-alpha-2 release? Especially for work, an extra computer i'd understand and still even then this question should be in the Ubuntu 10.10 Maverick Testing discussion.


Anyways about your problem, When you say you can't boot what exactly do you mean? Are there any errors?

---

### Post by bovender on 2010-06-21
Sorry, typo in haste, I meant to say 10.04, the current stable release.

The disk is formatted as Ext4.

The system boots, I get a weird-looking Gnome login screen (different visual style, much simpler) with a message in the top-right corner about incorrectly configured gnome-power-manager. When I try to login, I get a black screen for a few seconds, then the weird Gnome login screen again.

I booted from a 9.10 live CD and found that the / drive has "0 bytes" free. I deleted several large files, and still "0 bytes free". I guess this is hinting at the problem.

Thanks again for any help. I'm kind of in a desperate situation here.

If this can't be fixed via software repair, I guess I'll buy a new hard drive, install Ubuntu on it, and copy back my home folder.

Thanks a million


PS: (On a side note: When I hold SHIFT while booting and select the root console as recovery option, I get root access to the entire drive?! If that is possible, then why do I bother with a login password?!)

---

### Post by dim3000 on 2010-06-21
> **lazy_leukocyte said:**
> Sorry, typo in haste, I meant to say 10.04, the current stable release.

The disk is formatted as Ext4.

The system boots, I get a weird-looking Gnome login screen (different visual style, much simpler) with a message in the top-right corner about incorrectly configured gnome-power-manager. When I try to login, I get a black screen for a few seconds, then the weird Gnome login screen again.

I booted from a 9.10 live CD and found that the / drive has "0 bytes" free. I deleted several large files, and still "0 bytes free". I guess this is hinting at the problem.

Thanks again for any help. I'm kind of in a desperate situation here.

If this can't be fixed via software repair, I guess I'll buy a new hard drive, install Ubuntu on it, and copy back my home folder.

Thanks a million


PS: (On a side note: When I hold SHIFT while booting and select the root console as recovery option, I get root access to the entire drive?! If that is possible, then why do I bother with a login password?!)

That's only possible from a cd and that's turned on by default on purpose in case you forget your root password.

---

