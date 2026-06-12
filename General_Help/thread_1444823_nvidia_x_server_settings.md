---
title: "nvidia x server settings"
date: 2010-04-01
forum: General Help
---

### Post by warrenis1234 on 2010-04-01
Hi, when I connect my laptop to my tv, the nvidia settings allow me to show it on the screeen, but its stretched across both my monitor and my tv in the twin screen setting

when i try the separate screen setting so the screen isnt cut in half, it does not work

it did work once, and ive been trying ever since to figure out what i did..  does anyone know?



I would like to either have both screens visible as a whole and whatever i do on the monitor, show up on the tv..  or to have the monitor blanked out completely and have it run soley from the tv

thanks

---

### Post by audiomick on 2010-04-01
Hallo.
I am  not completely sure about this, but I think you need to do this.
In the terminal
```
gksu nvidia-settings
```
and enter your password (the one you use to log in)

In this window
[ATTACH]152123[/ATTACH]

click on the "configure" button next to where it says "twinview"

In the pop up
[ATTACH]152124[/ATTACH]
select disable.

You might want to make a backup of /etc/X11/xorg.conf before you mess around, in case it all goes pear shaped.

---

### Post by warrenis1234 on 2010-04-01
well that was pretty freakin simple.  i hate when that happens.

well um.. thanks.  and thanks for the quick reply

---

### Post by Quentumknight on 2010-07-18
I would like to do quite the same as that, but options other than "Separate X-screen" (that require to restart X)  are in gray and can't be selected. Also, it seems that the configuration file doesn't get saved, as I have to configure my screen from 800X600 to his normal 1440X900 each time I start the computer.

The strangest thing here for me is that I am not even using a separate screen. (I don't need that) but still can't deactivate the separate screen mode.

Thanks for helping me...

---

