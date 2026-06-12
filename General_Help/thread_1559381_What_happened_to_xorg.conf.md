---
title: "What happened to xorg.conf"
date: 2010-08-23
forum: General Help
---

### Post by measekite on 2010-08-23
I am currently running Jaunty 9.04 and find the xorg.conf in /etc/X11.

I just booted Lucid 10.04 from the Live CD just to take a look at things.  I could no longer find xorg.conf any place in the booted file system.

Does anybody know where to find this information?

---

### Post by mhgsys on 2010-08-23
xorg.conf in 9.04/9.10/ 10.04 is not longer the standard... you can generate one.. it will use it when it's there.


 here's how to do that;


```
Switch to a tty ( press ctrl+alt+f1 (f2,f3 etc)
```
login with your username and password.

stop gdm with
```
sudo service gdm stop
```

then generate a xorg.conf with 
```
sudo Xorg -configure
```

this will create a xorg.conf.new in your home directory)
move the auto-generated xorg.conf.new to /etc/X11/xorg.conf


```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```

Make changes you want to try 
```
sudo nano /etc/X11/xorg.conf
```
and start gdm again with

```
sudo service gdm start
```

---

