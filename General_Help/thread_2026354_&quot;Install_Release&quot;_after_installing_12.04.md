---
title: "&quot;Install Release&quot; after installing 12.04"
date: 2012-07-15
forum: General Help
---

### Post by mkstallings1 on 2012-07-15
I just installed 12.04 from usb, and after logging in for the first time, I have an icon at the top of the unity bat that says "Install Release."  That's what I just did.  What gives?  I have no removable media still plugged in, so I know I'm not accidentally still in live mode.

---

### Post by lolpenguin on 2012-07-15
The installer tool (Ubiquity) somehow got included in your installation.
Right-click the icon, click Unlock from Launcher, then
```
sudo apt-get purge ubiquity*
```

---

### Post by mkstallings1 on 2012-07-15
Thanks, that fixed it.

---

### Post by irv on 2012-07-15
Why don't you mark this thread as solved:
[ATTACH]221289[/ATTACH]

---

