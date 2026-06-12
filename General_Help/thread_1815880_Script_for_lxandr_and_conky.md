---
title: "Script for lxandr and conky"
date: 2011-08-01
forum: General Help
---

### Post by Rodney9 on 2011-08-01
Hello, I am using Xubuntu 10.10 on my Toshiba Laptop, when I start it it loses its resolution every few days.

I have to then run lxrandr and choose the correct resolution, then kill conky, because it is now in the middle of the screen, then restart conky.

Is there a script I could run to replicate this process

1. Reset resolution to 1366 x 768
2. Kill conky
3. Start conky

Thanks for any and all help,
Rodney

---

### Post by fdrake on 2011-08-01
> **Rodney9 said:**
> Hello, I am using Xubuntu 10.10 on my Toshiba Laptop, when I start it it loses its resolution every few days.

I have to then run lxrandr and choose the correct resolution, then kill conky, because it is now in the middle of the screen, then restart conky.

Is there a script I could run to replicate this process

1. Reset resolution to 1366 x 768
2. Kill conky
3. Start conky

Thanks for any and all help,
Rodney

before attempting to runn a script all the time we should try to fix the problem.


try this:

```
locate xorg.conf
```

do you see a file similar to "/etc/X11/xorg.conf.failsafe"?

if so copy it and edit it.

```
cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf.failsafe.bk
gedit /etc/X11/xorg.conf.failsafe
```

add 
[HTML]SubSection "Display"
              Virtual 3600 1200
       EndSubSection[/HTML]
like it says [in here]("https://wiki.ubuntu.com/X/Config/Resolution") before the EndSection

---

### Post by fdrake on 2011-08-01
for the script this may help:

```

cat > change_res.sh
-----------------------------------------------
#!/bin/bash
xrandr --output LVDS --mode 1366 x 768
xrandr --output VGA1 --mode 1366 x 768

#do not know what kind of screen u have

id=$( ps -e | grep conky | cut -d " " -f 2 )
echo $id
kill -9 $id
conky &
--------------Contr+C--------------------------

sudo chmod +x change_res.sh
./change_res.sh

```

---

### Post by Rodney9 on 2011-08-01
> **fdrake said:**
> before attempting to runn a script all the time we should try to fix the problem.


try this:

```
locate xorg.conf
```

do you see a file similar to "/etc/X11/xorg.conf.failsafe"?

if so copy it and edit it.

```
cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf.failsafe.bk
gedit /etc/X11/xorg.conf.failsafe
```

add 
[HTML]SubSection "Display"
              Virtual 3600 1200
       EndSubSection[/HTML]
like it says [in here]("https://wiki.ubuntu.com/X/Config/Resolution") before the EndSection

I get this -

```
$ locate xorg.conf
/home/lone/xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/X11/xorg.conf.d/60-magictrackpad.conf
/usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
/usr/share/man/man5/xorg.conf.5.gz

```

---

### Post by fdrake on 2011-08-01
> **Rodney9 said:**
> I get this -

```
$ locate xorg.conf
/home/lone/xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/X11/xorg.conf.d/60-magictrackpad.conf
/usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
/usr/share/man/man5/xorg.conf.5.gz

```

backup and edit /home/lone/xorg.conf 
you will have to set a lower resolution than the one i posted

---

