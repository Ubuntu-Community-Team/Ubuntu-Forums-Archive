---
title: "Boot ok, GDM blank screen, startx-workaround"
date: 2009-12-20
forum: General Help
---

### Post by TheFinePrint on 2009-12-20
I had [this issue]("http://ubuntuforums.org/showthread.php?t=1293255&page=3") with regular Ubuntu on a Dell laptop, and prerelease Karmic.

I have also tried Ubuntu Netbook Remix karmic on an EEE 1000HE, and get the same issue:

* Live USB works
* Boot after install works
* **GDM never loads. I only get a blank screen, and sometimes the X-cursor**
* I can work around this with alt+f2, log in, kill X, and startx

The latter is not good enough, so I hope that some of you might have a solution, otherwise I will have to fall back on Jaunty.

---

### Post by lidex on 2009-12-29
Try this in a terminal:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

Now reboot!

More here:
[http://ubuntuforums.org/showthread.php?t=1253012]("http://ubuntuforums.org/showthread.php?t=1253012")
[http://ubuntuforums.org/showthread.php?t=1213785]("http://ubuntuforums.org/showthread.php?t=1213785")
[http://ubuntuforums.org/showthread.php?t=1259121]("http://ubuntuforums.org/showthread.php?t=1259121")

---

