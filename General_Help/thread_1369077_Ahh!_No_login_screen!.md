---
title: "Ahh! No login screen!"
date: 2009-12-31
forum: General Help
---

### Post by Skinnybill on 2009-12-31
I was installing a Mac style theme on Ubuntu Karmic and i found after i did a reboot that my login screen doesnt appear! When selecting ubuntu from the GRUB loader, i see the ubuntu logo, as normal, and then i just get a black screen with the mouse. i can move the mouse but have nothing to click etc. i have pressed every button on the keyboard, left it for 1 hour and still nothing has happened. The only thing that i can do is hit the power button, the ubuntu logo appears again and shuts down.
any help?
--
Also i have tried running the older versions from GRUB (as each time you update it adds another option to GRUB) but still the same. Also, i can login to recovery mode, but i dont know what to do from there! Im on my windows drive at the mo, and im considering installing ubuntu as a partition on this drive (my ubuntu is installed on a seperate HD, not partitioned)

---

### Post by danastasio on 2009-12-31
when you boot and fail to get the screen, can you get into a console with CTRL+ALT+F2 ?

if you can, try running 

```
sudo service gdm restart
```

this will restart the GDM service, which is sometimes all that is needed, this will respawn the session in the tty7 terminal, so dont be freaked out if it goes (and stays black) again. just go back to the first one. You've actually got 6 consoles working at any given time, so dont be afraid to switch between them. 

If that doesn't work post the output of

```
sudo cat /etc/X11/xorg.conf
```

I'm willing to bet you were mucking about in the root filesystem, do you know what directories you were working in?

---

### Post by Skinnybill on 2010-01-01
Yes, i can get into console.
```
sudo service gdm restart
```
 did nothing. the screen flickered, i checked console 7 and i still only had the mouse.
So i run ```
 sudo cat /etc/X11/xorg.conf
``` and this was the output...
> Section "Screen"
        Identifier  "Default Screen"
        Default Depth 24
EndSection

Section "Module"
         Load "glx"
EndSection

Section "Device"
        Identifier "Default Device"
        Driver "nvidia"
        Option "NoLogo"  "true"
EndSection

Also im not sure what directories they were but i had installed and modifed a theme, and also installed a Mac-Style dock, along the lines of "_____ window manager"

---

### Post by Skinnybill on 2010-01-01
bump

---

