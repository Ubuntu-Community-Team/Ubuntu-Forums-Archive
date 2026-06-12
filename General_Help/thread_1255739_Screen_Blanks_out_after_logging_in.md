---
title: "Screen Blanks out after logging in"
date: 2009-09-01
forum: General Help
---

### Post by SteveKickert on 2009-09-01
I changed the resolution of my monitor and now when I login the screen goes blank right after logging in.  I tried doing the stuff in the following post:
[http://ubuntuforums.org/showthread.php?t=842847](http://ubuntuforums.org/showthread.php?t=842847)

However, it did not fix the issue.  

Any ideas?

---

### Post by tuxxy on 2009-09-01
If you can boot to a prompt did you try to reconfigure the xorg

```
sudo dpkg-reconfigure xserver-xorg
```

If no prompt then run the Live CD and select recover mode and then select XFIX at the next screen.

---

### Post by SteveKickert on 2009-09-01
Thanks.  Tried that too but it did not help.

---

