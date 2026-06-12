---
title: "How to delete files from another file system?"
date: 2010-10-24
forum: General Help
---

### Post by museumoftime on 2010-10-24
When I boot up my Ubuntu system I get the following error message:
Install Problem The configuration defaults for Gnome Power Management have been installed incorrectly

I found the following posting and this describes what also happens to my system
[https://answers.launchpad.net/ubuntu/+source/gnome-power-manager/+question/111256](https://answers.launchpad.net/ubuntu/+source/gnome-power-manager/+question/111256)

I've created a recovery disk by using a memory stick from which I can boot.  I can mount the old filesystem (HD).  When I navigate, with the file browser, into one of the folder on the the HD and try to delete messages I get the following error message - 'Error removing file: Permission denied'.

I guess I need to log / tell those files the root password from the system installation as per the version on the HD.  But how do I do this?

There is plenty of stuff that I can simply delete so no need to recover first just looking for way to delete.

Thanks for any pointers.

---

### Post by efflandt on 2010-10-24
Use **sudo** to rm files as root.  If using the default ubuntu user from install CD/usb, no password is needed for sudo.  Just make sure that you are in the proper directory on the proper disk before rm'ing files.

If you want to want midnight commander (mc) text based file browser mentioned in one reply there, you may need to install mc (not sure if it is on install CD/usb).  Then you could try **sudo mc**

Sounds like you may need to do some shrinking and expanding of partitions (note that moving the beginning of a partition can take many hours).

---

### Post by museumoftime on 2010-10-24
Thanks Efflandt!!  I didn't realise it was so easy -- after deleting a good piece of data I just managed to boot back into the system.  I'll need to do better file management in the future that this won't happen again.  Thanks!

---

