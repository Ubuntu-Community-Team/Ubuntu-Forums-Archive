---
title: "csh will not authenticate"
date: 2010-05-29
forum: General Help
---

### Post by xfilecsm on 2010-05-29
Just installed ubuntu studio Lucid, and installed csh in order to install XEphem. When I open a terminal and switch to csh to run the install script, I su root and enter my password, but it looks like nothing is being typed, and when I press enter, immediately the authentication failure message appears. I did not have this problem with karmic. Anyone got ideas for help, aside from reinstalling karmic?

---

### Post by spibou on 2010-05-29
Can you switch to root using a different shell ? Then you can do that and as root start csh. You can also try```
sudo install-script
```or perhaps```
sudo csh install-script
```If you show us the first few lines of the install script we can tell you which one.

---

### Post by luigi_mb on 2010-05-29
> **xfilecsm said:**
> Just installed ubuntu studio Lucid, and installed csh in order to install XEphem. When I open a terminal and switch to csh to run the install script, I su root and enter my password, but it looks like nothing is being typed, and when I press enter, immediately the authentication failure message appears. I did not have this problem with karmic. Anyone got ideas for help, aside from reinstalling karmic?

Don't use "su -c ...". Use "sudo ..."

/luigi

---

### Post by xfilecsm on 2010-05-30
Thanks everyone! sudo took care of that!

---

