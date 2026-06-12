---
title: "init / telinit does not seem to work"
date: 2010-01-25
forum: General Help
---

### Post by balameenu on 2010-01-25
I just installed my machine with ubuntu 9.04.  When I run "init 3" or "telinit 3", nothing happens.  I need to exit the X server to install a video driver.

Not sure what I am doing wrong.  Any help is appreciated.

---

### Post by falconindy on 2010-01-25
Ubuntu doesn't use runlevels. You need to stop gdm:
```
sudo service gdm stop
```

---

### Post by balameenu on 2010-01-25
gdm stop hangs with some message about Checking Reserve Battery!

Anyway, I did 'init 1', installed the driver and everything seem to be okay now.

Thank you.

---

### Post by hemimaniac on 2010-01-26
I have had similar problems in Linux Mint 7 ( 9.04 ) and the telinit 3 needs to be run as root or sudo telinit 3

---

