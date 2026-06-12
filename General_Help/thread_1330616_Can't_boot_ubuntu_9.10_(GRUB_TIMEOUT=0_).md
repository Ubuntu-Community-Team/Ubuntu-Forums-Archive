---
title: "Can't boot ubuntu 9.10 (GRUB_TIMEOUT=0 )"
date: 2009-11-18
forum: General Help
---

### Post by dpc_90 on 2009-11-18
I am using Ubuntu 9.10 (64 bit) with Grub 2.

I changed the default menu entry Windows 7 and I wanted to hide the menu. I uncommented the line GRUB_HIDDEN_TIMEOUT=0, then I executed "update-grub", but it didn't work - the boot menu was displayed at the same.

As it didn't work, I changed GRUB_TIMEOUT from 10 (default value) to 0. Now I can't display the boot menu anyway, even if I press "shift" or "esc", so I can't boot Ubuntu (as I said above, Windows 7 is the default OS).

I tried to change GRUB_TIMEOUT back to 10 using the Live CD, but it doesn't allow me to change the file /etc/default/boot, because I'm not logged in as root user.

What should I do to change GRUB_TIMEOUT back to 10? Can I do it using the Live CD? How?

Thank you very much!

---

### Post by sisco311 on 2009-11-18
Boot the LiveCD.

Press Alt+F2 and run 
```
gksu nautilus
```

this will start the file manager as root.

Mount the Ubuntu partition an navigate to /media/<UbuntuPartition>/boot/grub directory. Open the grub.cfg file and set the timeout to 10:
```
...
 
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  **set timeout=10**
fi

```

Reboot in Ubuntu, set the HIDDEN_TIMEOUT to 3 and GRUB_TIMEOUT 0 and run update-grub.

---

### Post by dpc_90 on 2009-11-18
It doesn't allow me to modify the file grub.cfg!!! It says I'm trying to write in a read-only disc...

---

### Post by sisco311 on 2009-11-18
> **dpc_90 said:**
> It doesn't allow me to modify the file grub.cfg!!! It says I'm trying to write in a read-only disc...

d'oh! damn gedit. :)


open a terminal (Applications -> Accessories -> Terminal)

type:
```
sudo nano
```
type a Space and drag the file (grub.cfg) in the terminal window.

you should see something like this:
```
sudo nano /media/<whatever>/boot/grub/grub.cfg
```

/media/<whatever>/boot/grub/grub.cfg is the path to the file.

press enter to open the file in nano text editor, edit the timeout, press Ctrl+x, y, Enter to save it and exit.

reboot  **in Ubuntu, set the HIDDEN_TIMEOUT to 3 and GRUB_TIMEOUT 0 and run update-grub.**

---

### Post by dpc_90 on 2009-11-18
Ok, that worked nicely, thank you. But now I can't boot Ubuntu once again, because menu is not being displayed again... What key should I press to display the menu?

---

### Post by sisco311 on 2009-11-18
> **dpc_90 said:**
> Ok, that worked nicely, thank you. But now I can't boot Ubuntu once again, because menu is not being displayed again... What key should I press to display the menu?

Shift, anyway set  GRUB_TIMEOUT to 1 ;)

---

### Post by dpc_90 on 2009-11-18
Shift doesn't work... When I press it Windows 7 boots normally...

---

### Post by JBAlaska on 2009-11-18
Try this [Thread](http://ubuntuforums.org/showthread.php?t=1302743)

P.S. If you want to use gedit use "gksudo" not "gksu"

You can do this with a GUI using SUM (StartUp-Manager):
```
sudo apt-get install startupmanager
```

---

### Post by sisco311 on 2009-11-18
> **JBAlaska said:**
> P.S. If you want to use gedit use "gksudo" not "gksu"

gksudo is just a symbolic link to gksu
```
ls -al /usr/bin/gksudo
```

---

