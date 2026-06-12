---
title: "logout from text terminal alt+f1"
date: 2011-10-04
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-10-04
is there a command to fully logout of Ubuntu without a reboot from a text terminal (alt + control + F 1) that will also logout of the graphical part (alt + control + F 7)?

this is for when something crashes and the only thing available is a text terminal or a hard shut down.

---

### Post by tomodachi on 2011-10-04
well back in the old days one could restart the graphical parts of your linux systems (the X server and window manager)

by pressing ctrl + alt + backspace. 

But ubuntu has that disabled by default

[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

will give you an idea on what file to edit to enable it

~tomodachi

---

### Post by spiky001 on 2011-10-04
I managed from tty1 ```
sudo /etc/init.d/gdm stop
``` But i cant get it to start again I had to reboot from tty1. Maybe some one can fix the next part?

---

### Post by dave01945 on 2011-10-04
you should try 

```
sudo /etc/init.d/gdm restart
```

allso you should be able to activate ctrl-alt-backspace from keyboard options under layout options

---

### Post by SE7EN-LOCSTA on 2011-10-04
this dontzap program is unable to be downloaded in 11.10.  

E: Unable to locate package dontzap

also, trying to manually add it to xorg.conf as stated in page resulted in me opening a blank file, perhaps it is moved in 11.10?



after i locate a pen to write down the text terminal command, i am going to try to reproduce the crash and see if that works. will report back when completed.

thanks for the prompt replies. :)

---

### Post by SE7EN-LOCSTA on 2011-10-04
crash went more quickly than i thought. went to login, accidentally chose old gnome.. went to logout to get on new gnome.. crash.

text terminal: sudo /etc/init.d/gdm restart

etc/init.d/gdm command not found.


any other suggestions?

---

### Post by spiky001 on 2011-10-04
```
 sudo /etc/init.d/gdm restart
```

---

### Post by haqking on 2011-10-04
> **SE7EN-LOCSTA said:**
> crash went more quickly than i thought. went to login, accidentally chose old gnome.. went to logout to get on new gnome.. crash.

text terminal: sudo /etc/init.d/gdm restart

etc/init.d/gdm command not found.


any other suggestions?

you are in 11.04 or 11.10 right ?

```
sudo service gdm restart
```

or just

```
sudo stop gdm
``` 
followed by 
```
sudo start gdm
```

---

### Post by SE7EN-LOCSTA on 2011-10-04
sudo service gdm restart = unknown service gdm
sudo stop gdm = unknown job gdm


frustrations. now upon login to gnome, i am greeted by only wallpaper. only thing diff/new was my accidental login to old gnome. am almost ready to give up and go back to good old 10.10 with all the troubles ive had with the 11 series.

---

