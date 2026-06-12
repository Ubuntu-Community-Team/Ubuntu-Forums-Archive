---
title: "X session of 16 bit color depth in Ubuntu 10.10"
date: 2011-06-22
forum: General Help
---

### Post by gunsten on 2011-06-22
To play an old win95 game I had to run it through a sub-session of Xserver, using Xephyr to provide the 16 bit color depth needed to show some of the graphics in the game.

This worked well then, but now when I try my old script launching the game it is not working. This must be since the 10.10 upgrade, and I can't think of any other major changes.

Some troubleshooting made me realize that the game does start in 24 bit, through wine directly or running it through a X session created with Xephyr - but not in 16 bit as earlier.

This is what I did to run it earlier:

```
Xephyr :1 -ac -screen 800x600x16&
DISPLAY=:1 wine <game file> &
```Now I receive this error message:

```
1 XSELINUXs still allocated at reset
SCREEN: 0 objects of 76 bytes = 0 total bytes 0 private allocs
DEVICE: 0 objects of 16 bytes = 0 total bytes 0 private allocs
CLIENT: 0 objects of 160 bytes = 0 total bytes 0 private allocs
WINDOW: 0 objects of 28 bytes = 0 total bytes 0 private allocs
PIXMAP: 1 objects of 8 bytes = 8 total bytes 0 private allocs
GC: 0 objects of 44 bytes = 0 total bytes 0 private allocs
CURSOR: 0 objects of 4 bytes = 0 total bytes 0 private allocs
CURSOR_BITS: 0 objects of 4 bytes = 0 total bytes 0 private allocs
DBE_WINDOW: 0 objects of 12 bytes = 0 total bytes 0 private allocs
TOTAL: 1 objects, 8 bytes, 0 allocs
1 PIXMAPs still allocated at reset
PIXMAP: 1 objects of 8 bytes = 8 total bytes 0 private allocs
GC: 0 objects of 44 bytes = 0 total bytes 0 private allocs
CURSOR: 0 objects of 4 bytes = 0 total bytes 0 private allocs
CURSOR_BITS: 0 objects of 4 bytes = 0 total bytes 0 private allocs
DBE_WINDOW: 0 objects of 12 bytes = 0 total bytes 0 private allocs
TOTAL: 1 objects, 8 bytes, 0 allocs
1 DAMAGEs still allocated at reset
TOTAL: 0 objects, 0 bytes, 0 allocs
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  1199
  Current serial number in output stream:  1203
1 XSELINUXs still allocated at reset
SCREEN: 0 objects of 76 bytes = 0 total bytes 0 private allocs
DEVICE: 0 objects of 16 bytes = 0 total bytes 0 private allocs
CLIENT: 0 objects of 160 bytes = 0 total bytes 0 private allocs
WINDOW: 0 objects of 28 bytes = 0 total bytes 0 private allocs
PIXMAP: 1 objects of 8 bytes = 8 total bytes 0 private allocs
GC: 0 objects of 44 bytes = 0 total bytes 0 private allocs
CURSOR: 0 objects of 4 bytes = 0 total bytes 0 private allocs
CURSOR_BITS: 0 objects of 4 bytes = 0 total bytes 0 private allocs
DBE_WINDOW: 0 objects of 12 bytes = 0 total bytes 0 private allocs
TOTAL: 1 objects, 8 bytes, 0 allocs
1 PIXMAPs still allocated at reset
PIXMAP: 1 objects of 8 bytes = 8 total bytes 0 private allocs
GC: 0 objects of 44 bytes = 0 total bytes 0 private allocs
CURSOR: 0 objects of 4 bytes = 0 total bytes 0 private allocs
CURSOR_BITS: 0 objects of 4 bytes = 0 total bytes 0 private allocs
DBE_WINDOW: 0 objects of 12 bytes = 0 total bytes 0 private allocs
TOTAL: 1 objects, 8 bytes, 0 allocs
1 DAMAGEs still allocated at reset
TOTAL: 0 objects, 0 bytes, 0 allocs
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
```Thankful for any help or any clues to what may have caused this change.

---

