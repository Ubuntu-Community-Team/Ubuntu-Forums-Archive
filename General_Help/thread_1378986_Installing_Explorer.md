---
title: "Installing Explorer"
date: 2010-01-12
forum: General Help
---

### Post by clevechan on 2010-01-12
I am trying to make wine work for explorer. I followed some instructions on this link

[http://ubuntuforums.org/showthread.php?t=670662](http://ubuntuforums.org/showthread.php?t=670662)

To follow this link, I am supposed to 

cd ~/ies4linux/ie6
cp user.reg ~/user.reg.old
gedit user.reg

1st and 2nd line went well

3rd line when I try to execute the command

gedit user.reg

(gedit:2573): Gtk-WARNING ** cannot open display

I then /ies4linux/ie6# ls

dosdevices(in blue)  drive_c(in blue)  system.reg(in white)  userdef.reg(in green)  user.reg

That is what I see

Any suggestions?

---

### Post by fancypiper on 2010-01-12
If you need root privilages, try sudo nano <file to edit> rather than gedit. or gksudo may work.

If you can't successfully complete a step, it does no good to continue on with the instructions.

---

### Post by clevechan on 2010-01-12
> **fancypiper said:**
> If you need root privilages, try sudo nano <file to edit> rather than gedit. or gksudo may work.

If you can't successfully complete a step, it does no good to continue on with the instructions.

Thank fancypiper. I managed to edit the file....but...

I installed explorer 6 ... but there is no address bar...

---

### Post by fancypiper on 2010-01-12
IIRC, I had the same problem, so I can't help on that.

Rather than chasing down bugs in wine/IE, I just use Opera, Epiphany, Galeon, Firefox, Links2 and Google Chrome.  Usually one of these will render a page OK.

---

