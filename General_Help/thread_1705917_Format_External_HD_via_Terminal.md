---
title: "Format External HD via Terminal"
date: 2011-03-13
forum: General Help
---

### Post by deanjm1963 on 2011-03-13
I have an external HD - 1gb Toshiba USB 3.0 drive. I have no problems formatting it with Disk Utility to ext3/4, it formats very quickly, but if I choose ext2 it takes nearly 25 minutes. Any other file system takes around 7-8 minutes.

I had no problem with 10.04 - has something changed the way 10.10 uses ext2? Also, it's not just this particular drive, it's ANY drive that I have.

I use JFS as my main file system, and since Disk Utility doesn't show JFS in its format options I would like to know how to format the external drive as JFS via terminal.

All I need to know is how to format it, give it the label "removable" and I'm fine from there. 

I have tried using GParted on 2 different systems to do it, but with 10.10 I get errors, the drive will format as JFS but on mounting it gives error messages about bad blocks - again, it's not just this particular removable drive, I have 4 of them.

The drive appears as /dev/sdb1

Any help would be greatly appreciated.

---

