---
title: "Failed Ubuntu 12.04 instrall"
date: 2012-05-19
forum: General Help
---

### Post by eltont on 2012-05-19
I have downloaded Ubuntu 12.04 and created a CD. I tried to load this on an IBM Think Center which has Windows XP. The install started after a few mins an error message appeared.
Tried rebooting twice.

File system check or mount failed
A maintenance shell will now be started
Control-D will terminate this shell and
continue booting after re-trying file systems. Any
/proc/self/fd 9:21:/proc/self/fd 9:/sbin/su login: input/output error
mountall/starting
proc/self/fd/9:12:exec: mountal: input/output error

Can any one advise.

---

### Post by 2F4U on 2012-05-19
Am I right in assuming that the error message is the one that occurred during installation? On first thought, I would suspect either a bad download or a bad burn. Did you verify the checksum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by eltont on 2012-05-20
Thanks Beans.
Did test, indicated that there is an error in one file.
Tried to burn  another image and on verification reported that the image burn as not successful because of an error occured(error code 0x80004005)
Is this a code associated with my equipment or should I try another download and burn althogether?

---

### Post by GreatDanton on 2012-05-20
> **eltont said:**
> Thanks Beans.
Did test, indicated that there is an error in one file.
Tried to burn  another image and on verification reported that the image burn as not successful because of an error occured(error code 0x80004005)
Is this a code associated with my equipment or should I try another download and burn althogether?

Maybe you should try to install from Usb. I have burned many cd's and only about 70% of them works properly. Since then I usually install Linux from Usb and it never fails (for me it works 100%).

---

