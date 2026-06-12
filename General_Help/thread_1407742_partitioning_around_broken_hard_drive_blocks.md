---
title: "partitioning around broken hard drive blocks"
date: 2010-02-15
forum: General Help
---

### Post by ethan33 on 2010-02-15
It's pretty much as simple as that. I am simply wondering if anyone knows of a tutorial of some kind or can explain how to partition around, in order to exclude bad data blocks on a busted hard drive. This is on a computer I just set up to run Karmic Koala. On another forum someone mentioned that there is a way to do this, and that is the only way, to my knowledge to "fix" said hard drive.

On a complete side note, does anyone know if an Intel 965 is supposed to work with Karmic out of the box, if you will? I haven't gotten a chance to check it specifically for this, and there seems to be no mention of this chipset with Karmic on these forums.

---

### Post by darolu on 2010-02-15
You should be able to do it with Gparted (GUI) or parted (pay special attention to mkpart and mkpartfs), if you can't with parted try with fdisk:

[http://www.gnu.org/software/parted/manual/parted.html](http://www.gnu.org/software/parted/manual/parted.html)

[http://www.debian.org/releases/2.1/alpha/fdisk.txt](http://www.debian.org/releases/2.1/alpha/fdisk.txt)

You can check hardware compatibility here:

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

I think your 965 chipset should work fine out of the box.

---

### Post by ethan33 on 2010-02-15
Thanks for the information. I just bookmarked this page for future reference.

---

