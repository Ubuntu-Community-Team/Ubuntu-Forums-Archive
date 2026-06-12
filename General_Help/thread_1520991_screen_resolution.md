---
title: "screen resolution"
date: 2010-06-30
forum: General Help
---

### Post by oxygenfarm on 2010-06-30
I was given an HP Pavillion XH485 for use by my granddaughter, age 10. The machine is memory limited (370 MB). I loaded 10.04 but cannot get a screen resolution higher than 800x600.
System>Preferences>Monitor does not show a higher resolution.
I am not a computer expert! Is there any application for allowing a higher resolution?
Many thanks.

---

### Post by cavh on 2010-06-30
This sounds like a graphics driver issue. Click on System -> Administration -> Hardware drivers and see if any choices come up. See also [http://ubuntu-manual.org/]("http://ubuntu-manual.org/")

In future, suggest posting in the Absolute Beginnners Talk forum :p

---

### Post by oxygenfarm on 2010-07-02
Thanks, but neither fix works.
Does anyone know if I should download another driver?

---

### Post by cavh on 2010-07-06
I'd start by editing /etc/X11/xorg.conf by hand to bump up the resolution. Make a backup of this file first, then use this from a terminal:

```
sudo nano /etc/X11/xorg.conf

```

Make sure you insert only a resolution supported by the graphics chipset - see the HP website to find this out if you don't already know it. After saving the modified file, log out and back in for the new resolution to take effect.

---

### Post by oxygenfarm on 2010-07-06
Thanks very much, but the system reported that /etc/X11/xorg.conf did not exist!
Being a klutz, I then inserted an old Ubuntu 7.04 live CD disk, and got a full 1024x768 screen resolution!

---

### Post by cavh on 2010-07-07
On further invetigation, it would appear xorg.conf is no longer mandatory in Lucid.

Found this on another thread at [http://ubuntuforums.org/showthread.php?t=1505061]("http://ubuntuforums.org/showthread.php?t=1505061"):

In a terminal, type 

```
sudo  Xorg -configure
```

then 

```
cp /home/YOUR_USERNAME_HERE/xorg.conf.new  /etc/X11/xorg.conf
```

then log out and back in again.

---

### Post by oxygenfarm on 2010-07-07
Thanks again for your patience.
After executing "sudo Xorg -configure" I get a "fatal server error: server is already active for display 0".

---

### Post by cavh on 2010-07-08
Doh, I should've asked you to stop X first:

hit CTRL-ALT-F1. Your Gnome desktop will disappear and be replaced by a black screen with a command prompt. Log in using your usual user name and password, then type

```
sudo service gdm stop
``` and hit the enter key

then type

```
sudo Xorg -configure
``` and hit the enter key

then type

```
sudo cp /home/YOUR_USERNAME_HERE/xorg.conf.new  /etc/X11/xorg.conf
``` and hit the enter key

then type

```
sudo service gdm start
``` and hit the enter key

and you should be back to the usual graphical login screen.

---

### Post by oxygenfarm on 2010-07-09
Just to finalize our quest into video configuration: none of your good advice helped me, but thanks again for the patience.
After determining that an old Ubuntu 7.04 set the resolution correctly,but 10.04 could not,I tried Puppy Linux 5 and found that it has excellent tools for setting up the screen. I actually used their 1280x1024 resolution and it works great.

---

