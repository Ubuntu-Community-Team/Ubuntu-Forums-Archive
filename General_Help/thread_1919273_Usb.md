---
title: "Usb"
date: 2012-02-02
forum: General Help
---

### Post by danw_tx on 2012-02-02
Hi All -

I'm new here and realize this might not be the correct forum in which to post my question.   I didn't see any forum names that pertain to running linux from a USB drive so I figured I just start here.

My situation is as follows:
I've used NetBootin to create a 64-bit Ubuntu 11.10 install on a 16-GB USB drive, with persistence.  After performing some updates using APT, I got these messages, among others:
 
[LIST]
[*]cryptsetup: WARNING: failed to detect canonical device for overlayfs
[*]cryptsetup: WARNING: could not determine root device from /etc/fstab
[/LIST]
 Since the letters 'fs' are shown here, I went and looked at my fstab file, which is here:

ubuntu@ubuntu:~$ cat /etc/fstab
[INDENT] overlayfs   /         overlayfs   r         w          0  0
 tmpfs        /tmp    tmpfs        nosuid,nodev   0  0
[/INDENT] 
I'd just like to know what all the above means.  A few questions that come to mind are:
Should I be able to set a root device?
What kinds of files systems are the overlayfs and tmpfs?
Is it possible to resize USB drive partitions, using gparted, or something similar?

In spite of the warnings, I can boot just fine from the USB drive, connect to my wireless network, surf the web, etc., etc.

Please feel free to point me to a more appropriate forum and thanks in advance for your help.

~ Danw_tx

---

### Post by dragonfly41 on 2012-02-02
this points to same errors ..

[http://ubuntuforums.org/showthread.php?t=1805485](http://ubuntuforums.org/showthread.php?t=1805485)

---

