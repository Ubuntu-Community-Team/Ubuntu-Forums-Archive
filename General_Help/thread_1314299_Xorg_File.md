---
title: "Xorg File"
date: 2009-11-04
forum: General Help
---

### Post by RedSingularity on 2009-11-04
I herd in 9.10 there is no xorg.conf file?  Is this true.?  If so how do we configure our video cards??

---

### Post by lukeozade on 2009-11-04
On a fresh install there won't be an xorg file. If necessary you can create one (i have one that my nvidia card generated automatically as it still depends on xorg.conf).

> From wikipedia:
For a long time, editing xorg.conf was necessary for advanced input devices and multiple monitor output to work correctly. This was regarded to be a major usability obstacle. In modern systems this is seldom necessary, thanks to input hotplugging and the XRandR extension integrated into new X.org releases. It is still needed for devices from some manufacturers, notably NVIDIA and Wacom, whose drivers fail to provide support for those technologies.

Hope that explains this.

---

### Post by RedSingularity on 2009-11-04
Oh ok.  So i can still make one then.  Very good.  Thanks:)

---

### Post by Surrendermonkey on 2009-11-04
> **lukeozade said:**
> On a fresh install there won't be an xorg file. If necessary you can create one (i have one that my nvidia card generated automatically as it still depends on xorg.conf).



Hope that explains this.

Just to be sure, this means that if I create a xorg.conf it will override the current settings?

The reason being that I'm working with a sis mirage 3 chipset, which has an experimental driver that I know from my previous gentoo installation works with the current gnome, using the same kernel as Karmic.

Thanks for any input in advance

---

### Post by Giblet5 on 2009-11-04
> **Surrendermonkey said:**
> Just to be sure, this means that if I create a xorg.conf it will override the current settings?

The reason being that I'm working with a sis mirage 3 chipset, which has an experimental driver that I know from my previous gentoo installation works with the current gnome, using the same kernel as Karmic.

Thanks for any input in advance

Yes. X no longer requires an xorg.conf, but it will use one if it finds one.

Always debug your xorg.conf by flipping to the text console via Ctrl-Alt-F1 and running ```
sudo /etc/init.d/gdm stop
```

Use startx to start a simple session, then exit the one terminal window to return to the prompt. This way, any errors in your xorg.conf syntax are right there to read.

When it looks just right, turn gdm back on via ```
sudo /etc/init.d/gdm start ; exit
```

---

### Post by Surrendermonkey on 2009-11-04
After a bit of trial and (all of the tries in fact) error I have some more questions.  How would a standard xorg.conf look under ubuntu 9.10?  I tried copying one from a friends 9.10 ubuntu, adding in the Driver part. This produces the error Screen not found and module not loaded, I'm not  really sure what to do from here, any ideas?

---

### Post by Giblet5 on 2009-11-04
How long is a piece of string?

It depends on what you're trying to do.

I presume that you're just trying to specify a SiS driver. Right?

That could be as simple as ```
Section "Device"
    Identifier     "Video0"
    Driver         "sis"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Video0"
EndSection
```

and that will get the driver loaded. But there are [lots of options that are common to all SiS chips]("http://www.x.org/archive/X11R6.8.0/doc/SiS.html"), so you might want to add them, along with the more specialized options that the dri-capable chips have ```
Section "Device"
    Identifier     "Video0"
    Driver         "sis"
    Option         "Turboqueue" "true"
    Option         "NoYV12" "true"
    Option         "DRI" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Video0"
EndSection
```

---

### Post by grandtoubab on 2009-11-04
[http://www.x.org/wiki/ConfigurationHelp](http://www.x.org/wiki/ConfigurationHelp)

As root just run: X -configure.

I upgrade from 09.04 to 09.10 and my xorg files remain in /etc/X11
```

desktop:/etc/X11$ ls -alrt
total 120
-rw-r--r--   1 root root    13 2007-07-24 11:59 XvMCConfig
-rw-r--r--   1 root root   265 2008-05-14 02:10 Xsession.options
-rwxr-xr-x   1 root root  3730 2008-05-14 02:10 Xsession
-rw-r--r--   1 root root 17394 2008-05-14 02:10 rgb.txt
drwxr-xr-x   6 root root  4096 2008-07-02 12:21 fonts
-rw-r--r--   1 root root    14 2008-07-02 12:29 default-display-manager
drwxr-xr-x   2 root root  4096 2008-07-02 12:32 cursors
lrwxrwxrwx   1 root root    13 2008-10-17 22:10 X -> /usr/bin/Xorg
-rw-r--r--   1 root root  1253 2008-10-30 20:35 xorg.conf.dist-upgrade-200810302035
-rw-r--r--   1 root root  1441 2009-04-24 18:16 xorg.conf.dist-upgrade-200904241816
-rw-r--r--   1 root root  1439 2009-04-24 21:25 xorg.conf.20090424212552
-rw-r--r--   1 root root  1496 2009-05-18 15:27 xorg.conf.20090518152739
-rw-r--r--   1 root root   894 2009-05-18 15:28 xorg.conf.failsafe
-rw-------   1 root root   601 2009-08-26 19:44 Xwrapper.config
drwxr-xr-x   3 root root  4096 2009-08-26 20:02 xinit
-rw-r--r--   1 root root  1037 2009-08-26 20:20 xorg.conf.dist-upgrade-200908262020
-rw-r--r--   1 root root  1496 2009-09-20 10:34 xorg.conf.save
-rw-r--r--   1 root root  1499 2009-09-21 20:51 xorg.conf~
-rw-r--r--   1 root root  1524 2009-09-21 21:29 xorg.conf
drwxr-xr-x   2 root root  4096 2009-10-10 18:32 app-defaults
drwxr-xr-x   2 root root  4096 2009-10-15 17:31 xkb
drwxr-xr-x   2 root root  4096 2009-10-20 16:44 Xresources
drwxr-xr-x   9 root root  4096 2009-10-20 16:44 .
drwxr-xr-x   2 root root  4096 2009-10-26 17:32 Xsession.d
drwxr-xr-x 160 root root 12288 2009-11-04 19:45 ..
```

---

