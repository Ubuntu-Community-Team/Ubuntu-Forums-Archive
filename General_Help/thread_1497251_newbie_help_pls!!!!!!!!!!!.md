---
title: "newbie help pls!!!!!!!!!!!"
date: 2010-05-30
forum: General Help
---

### Post by danbuntu24 on 2010-05-30
hi guys i'm kinda new here... needed a little assistance:)
 
so i've downloaded ubuntu 10.04 and want too dual boot it with winxp (suddenly everything sucks)
 
i've properly burnt the live cd and also created the live usb but i simply cant boot from both. when I go to boot options in d bios it shows me
 
usb-hdd
usb-zip
usb-fdd etc..
 
ive booted from all above and also my dvd drive but nothing seems to work
 
I tried it on Virtual Box(on my comp) and booted it on my laptop and it worked fine
 
dsl and feather linux work flawlessly from their respective live cd's.
 
so pls help me join the gang!!:guitar:
 
 
 
 
P.S.: I have Comodo Time Machine that loads before xp so can that be causing the problem??:confused:

---

### Post by Ozymandias_117 on 2010-05-30
What are all the options you have in your boot menu?

Did you do the md5 checksum on the iso?

Are you getting any errors etc?

---

### Post by ankspo71 on 2010-05-30
Hi,
Did you go into your computer's bios, and tell your computer to boot from the cdrom before booting from the hard drive? Usually you press the DEL key as your comptuer starts up to enter the bios/setup. Once you are in there you look around for something like "boot priority" or "boot sequence" then select your cdrom entry then move it up so that it is first in line to boot. You should be able to do the same with your USB device too. Then you just need to save your changes and exit, then restart.

Here is some more information on this subject:
[https://help.ubuntu.com/7.04/installation-guide/i386/pre-install-bios-setup.html](https://help.ubuntu.com/7.04/installation-guide/i386/pre-install-bios-setup.html)
Hope this helps.

---

