---
title: "Cannot open/find ALSAmixer"
date: 2009-12-20
forum: General Help
---

### Post by BlueCanary9999 on 2009-12-20
Running Karmic 9.10 64bit on Lenovo Y530.  Sound used to work in Karmic, but not with all speakers, so I followed [this guide]("http://ubuntuforums.org/showpost.php?p=5460960&postcount=2"), which I had used to get them all working in Jaunty.  But when I got to the step that involves settings in ALSAmixer, the terminal returned "cannot open mixer: No such file or directory".  Since ALSA mutes sound initially, I currently have no sound and no way to adjust that.  I've tried alsamixergui and gnome-alsamixer, but the former has an error and the latter is blank.  So how do I get to ALSAmixer?

Thanks in advance!

[SOLVED]
See third post.

---

### Post by BlueCanary9999 on 2009-12-21
With the recent ALSA updates, I now have the ALSAmixer.  Problem solved.


[EDIT]
WAIT!  No.  I take that back.  The ALSAmixer, although present, only displayed a bar for master volume.  I figured I could solve this problem by again installing the stuff instructed by the guide.  After rebooting, I realized I lost ALSAmixer....  So back to square one.

---

### Post by BlueCanary9999 on 2009-12-22
Problem really solved.  See [here]("http://ubuntuforums.org/showpost.php?p=8540109&postcount=556"), specifically "You're running the Lucid mainstream kernel? I also installed linux-backports-modules-alsa-karmic as suggested here, and I don't know if that helped."

You can find the Lucid RC kernels [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").

---

