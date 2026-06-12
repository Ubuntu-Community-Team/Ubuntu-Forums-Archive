---
title: "Can't get a complete shutdown."
date: 2009-11-09
forum: General Help
---

### Post by Steve.G on 2009-11-09
Either via the menus in Gnome, or just manually running the shutdown command, I always get errors when I try to shut down, and then it never finishes, so my laptop battery sits there dying and the screen cooking.

This is a new issue since I upgraded from Jaunty to Karmic. I don't really know what other info would be helpful, so if you need more detail please let me know.

Here's what it looks like:

```
fsck from util-linux-ng 2.16
/dev/loop0 clean, xxxxxx/xxxxxxx files, xxxxxx/xxxxx blocks.
Ubuntu 9.10 <system name> tty1
ubuntu login:[xxxxx.xxxxx] Buffer I/O error on device loop0, logical block xxxxxxx
[xxxxx.xxxxx] Buffer I/O error on device loop0, logical block xxxxxxx
[xxxxx.xxxxx] Buffer I/O error on device loop0, logical block xxxxxxx
Aborting Journal on device loop0.
[xxxxx.xxxxx] Buffer I/O error on device loop0, logical block xxxxxxx
[xxxxx.xxxxx] Buffer I/O error on device loop0, logical block xxxxxxx
```

obviously the x's are numbers that change, though I notice that the first 4 errors are all in the same range.. only varying in the last two digits.

---

