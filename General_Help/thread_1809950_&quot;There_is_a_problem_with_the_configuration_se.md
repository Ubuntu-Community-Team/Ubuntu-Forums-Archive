---
title: "&quot;There is a problem with the configuration server&quot; After installing 11.04"
date: 2011-07-22
forum: General Help
---

### Post by robot85 on 2011-07-22
I did a fresh install (the installer erased 10.04 and installed 11.04) of Natty. Now as soon as I boot into Ubuntu I get the error "There is a problem with the configuration server....exited with status 256" This comes up before the log in screen, and once I type in my password, after as well.

Also, I'm getting the error “The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator.”

I cannot log in. I just get sent back to the log in screen.

I have searched and searched for a solution to both of these errors, and it seems that no one can find a solution to the configuration server error.

Please help... :(

---

### Post by Neobuntu on 2011-07-22
Things to try:```
df -h
``` ...and check drive space. Is it (or they) full?```

sudo apt-get -f install

sudo apt-get update

sudo apt-get dist-upgrade

sudo dpkg-reconfigure gnome-power-manager
```

Another idea, is just to back step, and then get it done faster, with an install of Linux Mint 11, instead.

USB vs. CD:

Are you using the alternate install? Are you using USB? Else, are you burning CD's slowly?

If you have a fast, and big enough, USB drive, of some sort, Google Linux Pen drive and see your options. [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

If you do have USB 2.0, but can not get your computer to boot by USB (and you're sure), then find PLOP (not the OS, but it's booter) and burn a boot CD, from the PLOP CD image. It will now let the computer boot USB, and you will not have to burn any more CD's.

---

