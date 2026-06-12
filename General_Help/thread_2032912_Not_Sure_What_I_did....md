---
title: "Not Sure What I did..."
date: 2012-07-24
forum: General Help
---

### Post by 1992drewski on 2012-07-24
Well, every thing was working fine or should I say awesome in Ubuntu 12.04 untill I messed it all up.

Screen resolution was fine, and everything was working the way it should. However, my Nvidia drivers were not working... I think.

I opened the Nvidia X server setting, and a window pops up promting me:
> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
So I was just like okay, and ran 'nvidia-xconfig' as root. It did something then promted me to restart the X server. I googled how to restart the X server in Ubuntu 12.04 and I found this command 
> sudo service lightdm restart
Without reading anything on the page at all I ran the command (not as root).

This pretty took a dump on my Ubuntu. Ubuntu works and all still... Im just using a 640x480 resolution. 

After I ran the command it exited the GUI and some words flashed on the screen... didn't really pay attention to what was there, but I can do it again if it helps you help me :-).

I restarted Ubuntu and a message came up right after singing in saying that it could not configure the monitor and you have to use this crappy resolution. 

It would be a HUGE help if someone could lend me a hand. I am working on developing Android apps, and it would be great if I could have this thing up and running asap. 

Thank you
Andrew

---

### Post by Bucky Ball on 2012-07-24
Have you looked in Additional Drivers? You may be able to remove the Nvidia driver and start again.

Also, when nvidia-config rewrote the xconfig file, it might have made a backup before doing so. You can have a look at that (in the same directory) and copy it back again (don't move it as then you won't have a backup).

You will find it has probably (re)written an xorg.conf file which can be found at:

```
/etc/X11/xorg.conf
```

Take a look with:

```
nano /etc/X11/xorg.conf
```

If that file is blank, it's not your problem. If it isn't, Look in the directory (dir /etc/X11) for something like:

```
/etc/X11/xorg.conf.bak
```

If you find it, then:

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

Control+X and 'y' to exit and save. Reboot.

The xorg.conf file is generally empty in newer releases but can be used to customise. If you had any tweaks in a custom xorg.conf file you'll need to retweak. If not, you can just make the file blank again by:

```
sudo nano /etc/X11/xorg.conf
```

... and delete everything.

---

### Post by efflandt on 2012-07-25
If you run 'sudo nvidia-xconfig' you could probably just log out of X, and then log back in.

But if you run the following command it has to be run from a console, not from X:

```
sudo service lightdm restart 
```

In other words do Ctrl+Alt+F1, run that command, then Alt+F7 to get back to X.

What nvidia card do you have?  If you have an older card, you might need to use an older nvidia driver instead of nvidia-current.

---

