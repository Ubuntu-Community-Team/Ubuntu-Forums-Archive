---
title: "Decompression problem with 9.10"
date: 2009-11-03
forum: General Help
---

### Post by M4rotku on 2009-11-03
Hey guys,

I recently burnt a 9.10 disk and when trying to boot from it I got an error saying something about a decompression problem.  So I figured that the disk didn't burn well and kept reburning it and trying again.  Would this problem be more likely caused by the .iso image being bad, the disk being bad, or the blanking/burning process being bad?

Much thanks,
M4rotku

---

### Post by undecim on 2009-11-03
have you tried the option from the LiveCD menu to check the disk for defects?

EDIT: Also, try the disk on another system, and if it works for that system, then run memtest (from the Ubuntu LiveCD menu) on the machine that isn't working.

---

### Post by alphaniner on 2009-11-03
My money would be on a bad burn.  But don't take my word for it.

You can test the iso by verifying the [md5sum]("http://releases.ubuntu.com/karmic/MD5SUMS").

If that worked, you can check the disc.  There should be an option to test the disc during boot.  If the boot menu of the disc does not come up and you have an existing install, insert the disc and open a terminal window.  Change to the directory where the disc is mounted (ie. /media/cdrom).  There should be a file md5sums.txt.  Run ```
md5sum -c md5sums.txt
```
to verify the disc.

---

