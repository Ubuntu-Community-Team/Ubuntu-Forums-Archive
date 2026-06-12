---
title: "Black screen ..."
date: 2011-02-26
forum: General Help
---

### Post by ka2r on 2011-02-26
Hello I have a Problem: After installing the driver on Intel (R) C33/G31 Express Chipset Family name and restart the screen goes black. Did not understand. At the same time I can scroll through the cube and run the console .. Tell me what to do to restore things back? Is it possible to roll back a driver?

---

### Post by seawolf167 on 2011-02-26
I don't know what you mean by "scroll through the cube", but if you only have console access (and you have a desktop gui installed), try the following commands

start the x server

```
sudo startx
```

restart gdm

```
sudo service gdm restart
```

reconfigure your xserver-xorg

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by WorMzy on 2011-02-26
> **seawolf167 said:**
> 
start the x server

```
sudo startx
```


No, don't use sudo with startx, just run it as a normal user.

---

