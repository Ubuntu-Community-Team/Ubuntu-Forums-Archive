---
title: "Ubuntu Boot Option Stuck on Boot Menu"
date: 2009-08-24
forum: General Help
---

### Post by Guymed on 2009-08-24
Hey. Yesterday I installed Ubuntu 9.04 on my computer to give it a try, but I wasn't so satisfied. So I uninstalled it through the Add/Remove Programs menu on Win XP. I rebooted the computer. It asked me select XP or Ubuntu although Ubuntu was gone. How do I remove it from the boot menu? Things to know just in case: installed through the wubi-like thing on the CD (through XP), uninstalled through add/remove, do not have XP disk, tried system restore (fail).

Please help!

---

### Post by tuxxy on 2009-08-24
Try uninstalling manually like in [this guide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?")

---

### Post by Guymed on 2009-08-24
Uhh, aahh somehow the deleted ubuntu folder was restored from my recycle bin and thats why, so I deleted it and it **should** no longer open the boot menu.

---

### Post by tuxxy on 2009-08-24
Uninstall as the guide says then reboot and have a look if its gone, then report back :D

---

### Post by Guymed on 2009-08-24
Boot into Ubuntu still shows, looks like my computer doesn't wanna play around.

---

### Post by P4man on 2009-08-24
you've deleted ubuntu, but you havent modified your bootloader yet. from the link tuxxy posted above:

> How do I manually uninstall Wubi?

Remove C:\ubuntu and C:\wubildr*.

**In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line.** For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via control_panel > system > advanced > startup_and_recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys, and remove the Wubi block. 

---

### Post by michy99 on 2009-08-24
Edit the boot.ini file and remove the entry for Ubuntu.

---

### Post by Guymed on 2009-08-24
> **P4man said:**
> you've deleted ubuntu, but you havent modified your bootloader yet. from the link tuxxy posted above:

I would do that but there is a problem... there is no boot.ini file anywhere in my computer.

---

### Post by michy99 on 2009-08-24
> **Guymed said:**
> I would do that but there is a problem... there is no boot.ini file anywhere in my computer.

It should be located at C:\boot.ini. Assuming that Windows is on your C: drive.

---

### Post by P4man on 2009-08-24
its  in the root of  your c:\ drive, but hidden and system file. 

So light a candle for Bill Gates and say 3 hail marries and ask mighty Windows to disclose to you the hidden inner secrets of its OS.. Or at least the boot configuration files :)

If that fails,  change the explorer / file manager settings to display  hidden, system dangerous and forbidden files ;)

---

### Post by Guymed on 2009-08-24
Yeah but how do I change the explorer settings?

---

### Post by Guymed on 2009-08-24
I found it by going to run then typing C:\boot.ini but when I try to save it after deleting the ubuntu line it says I can't because it's read only, but it's icon isn't visible so I can't access the properties and change the read-only setting.

---

### Post by michy99 on 2009-08-24
Here is the official Microsoft way to edit boot.ini:

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by P4man on 2009-08-24
And you didn't like ubuntu ? Heh.. 

here you go:

[http://www.extremetech.com/article2/0,2845,1838913,00.asp](http://www.extremetech.com/article2/0,2845,1838913,00.asp)

---

### Post by Guymed on 2009-08-24
> **P4man said:**
> And you didn't like ubuntu ? Heh.. 


It's not that I don't like it, I removed it because it's a bit hard juggling two OSes.

I think I got it to stop showing the boot menu, I'll try later.

---

### Post by ottosykora on 2009-08-27
yes and the boot.ini is also read only, so you have to change the attribute first. The delete the ubuntu line and save it.

---

