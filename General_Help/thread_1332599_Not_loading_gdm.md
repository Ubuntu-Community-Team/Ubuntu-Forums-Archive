---
title: "Not loading gdm"
date: 2009-11-20
forum: General Help
---

### Post by dyltman on 2009-11-20
Alright so I was messing around with my computer when the electricity went in my house so the computer got shut down. Now that I try to open up ubuntu insteed of getting greeted with the GDM gnome thing I get a terminal that covers the entire screen. Is there anyway to fix this?

Edit: I can log in on the terminal and edit stuff but I'm not good at the commands (newbie)

---

### Post by Hamchan on 2009-11-20
That's tty,

Try startx

---

### Post by dyltman on 2009-11-20
> **Hamchan said:**
> That's tty,

Try startx

didn't work, got FATAL ERROR: No screens found

edit: I think it was tty that loaded since there was a title called tty1

---

### Post by dyltman on 2009-11-20
I guess it means a full reinstall?

---

### Post by ajgreeny on 2009-11-20
You should reboot to recovery mode and try the xfix option at the menu that appears.  If that fails, and you have no important files that you have not backed up, then a reinstall is possible, but I imagine there are ways to get xorg back without that.

You could try reinstaling xserver-xorg, xorg, and perhaps any xorg drivers that you know you were using, eg xserver-xorg-video-ati or xserver-xorg-video-nv.

It must be worth a try, even if it's not successful.

---

### Post by dyltman on 2009-11-20
> **ajgreeny said:**
> You should reboot to recovery mode and try the xfix option at the menu that appears.  If that fails, and you have no important files that you have not backed up, then a reinstall is possible, but I imagine there are ways to get xorg back without that.

You could try reinstaling xserver-xorg, xorg, and perhaps any xorg drivers that you know you were using, eg xserver-xorg-video-ati or xserver-xorg-video-nv.

It must be worth a try, even if it's not successful.

Luckily enough I had just done a reinstall this morning so I suppose I could reinstall it all. I didn't have anything important yet

edit: I'm not a linux pro either so.

---

### Post by khelben1979 on 2009-11-20
If startx doesn't work, then it means that your X server configuration file isn't working.

Location for your X config file is here: > /etc/X11/xorg.conf

Tell us a little about your hardware by doing the following:
```
lspci
``` from the text console and share your output here.

Then we can determine what graphics chipset/card you have in there. When we know, we know where you can get them and how.

---

### Post by dyltman on 2009-11-20
> **khelben1979 said:**
> If startx doesn't work, then it means that your X server configuration file isn't working.

Location for your X config file is here: 

Tell us a little about your hardware by doing the following:
```
lspci
``` from the text console and share your output here.

Then we can determine what graphics chipset/card you have in there. When we know, we know where you can get them and how.

thanks but too late now :(

deleted the partition to install ubuntu once again :P

---

