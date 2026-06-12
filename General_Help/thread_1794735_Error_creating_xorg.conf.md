---
title: "Error creating xorg.conf"
date: 2011-07-01
forum: General Help
---

### Post by Lucas Malor on 2011-07-01
I tried to created xorg.conf with ```
sudo Xorg :1 -configure
``` and I get this error:
[http://dl.dropbox.com/u/33183126/xorg-configure.txt](http://dl.dropbox.com/u/33183126/xorg-configure.txt)

Briefly, no /etc/X11/xorg.conf was created, but ~/xorg.conf.new :
[http://dl.dropbox.com/u/33183126/xorg.conf.new](http://dl.dropbox.com/u/33183126/xorg.conf.new)

I think errors was raised because I don't use (and I don't want to use) nvidia propetary drivers. Now, I have some problems:

[LIST=1]
[*]Why /etc/X11/xorg.conf was not created?
[*]Why 3 monitors are present in ~/xorg.conf.new ?
[*]Why there's no modeline in ~/xorg.conf.new ?
[*]How can I add a modeline if there's no /etc/X11/xorg.conf ?
[/LIST]

---

### Post by dino99 on 2011-07-01
why do you want to create such a file ? Nowadays kernel directly deal with X.

But if you still want it then nvidia-settings is your boy.

sudo rm /etc/X11/xorg*

[http://askubuntu.com/questions/37761/xorg-conf-in-ubuntu-natty-11-04](http://askubuntu.com/questions/37761/xorg-conf-in-ubuntu-natty-11-04)

---

### Post by Lucas Malor on 2011-07-01
[list=1]
[*]I want xorg.conf because I want to add a modeline with 100 Hz refresh rate with 1024x768 resolution, that I'm sure my monitor supports (tested with Windows).
[*]I already installed nvidia-settings and it allow me to do nothing. IMO the cause  it's the same before (no proprietary blablabla)
[*]I have no /etc/X11/xorg* file
[/list]

---

### Post by whatthefunk on 2011-07-01
Why dont you just create your xorg file using nano or some other text editor?  You only need to add the bits that you need, not the entire configuration.

---

### Post by Lucas Malor on 2011-07-01
Well, I can try, but I'm sure I'll enter rescue mode very soon :P

---

### Post by whatthefunk on 2011-07-01
> **Lucas Malor said:**
> Well, I can try, but I'm sure I'll enter rescue mode very soon :P

Its easy.  Heres mine as sample:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31.5-48.5
        VertRefresh 40-70
        Option "dpms"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth 16
        Option "Accel"
        SubSection "Display"
                Depth 16
                Modes "1024x768"
        EndSubSection
        SubSection "Display"
        EndSubSection
EndSection

```

There are tons of guides for writing xorg.conf files on the net.  Do a few googles and Im sure youll find what you need. 

And normally if you make a mistake with something like monitor resolution, you dont enter rescue mode.  You just cant see properly.  Its easy to fix...just go in and delete your xorg.conf file.

---

### Post by whatthefunk on 2011-07-01
Some info that may help:

[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)
This seems to be the same as
```
man xorg.conf
```

[http://www.linuxforums.org/forum/desktop-x-windows/40987-xorg-how-set-refresh-rate-100hz.html](http://www.linuxforums.org/forum/desktop-x-windows/40987-xorg-how-set-refresh-rate-100hz.html)

---

### Post by Lucas Malor on 2011-07-04
Well, I found how to add modelines without creating a xorg.conf, but Ubuntu doesn't support this modeline. I'm quite sure under Windows XP I can use 1024x768@100hz. What I can do? My monitor is a Samsung SyncMaster 793s.


PS: if someone is interested, to add a modeline:

see the name of your output with xrandr
cvt [--reduced] WIDTH HEIGHT [REFRESH]
(don't use --reduced with CRT)
the output will be
ModeLine "MODE_NAME" PARAMETERS
xrandr --newmode "MODE_NAME" PARAMETERS
xrandr --addmode OUTPUT_NAME MODE_NAME

---

### Post by deserthowler on 2011-07-04
I created my last Xorg file by running an old live CD and using that.  In my case it was Ubuntu 6,10.  I copied it to my hard drive and tuned it.

Earl

---

