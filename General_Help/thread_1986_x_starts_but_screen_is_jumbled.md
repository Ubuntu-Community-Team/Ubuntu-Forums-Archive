---
title: "x starts but screen is jumbled"
date: 2004-10-24
forum: General Help
---

### Post by helios on 2004-10-24
hd install of Ubuntu went fine, did not see any X issues however, on reboot, when x tries to start, it is badly jumbled...like the vertical needs fixing in old TV's.  I restarted, did a text login and typed "start x" and "startx" but both said command not found.  I realize this may be a video card issue or a setting...I just need to know how to fix it.  this looks as if it may be a good distro.  I really want a chance to find out

thanx

helios

---

### Post by im_ka on 2004-10-24
```
sudo dpkg-reconfigure xserver-xfree86
```
hope this helps

---

