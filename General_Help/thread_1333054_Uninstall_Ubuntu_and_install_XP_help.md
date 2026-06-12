---
title: "Uninstall Ubuntu and install XP help"
date: 2009-11-21
forum: General Help
---

### Post by R3V3RB on 2009-11-21
I bought a PC that came with Ubuntu 9.04 intending on removing Ubuntu and installing XP i have a XP disk that works but Ubuntu wont read ti and wont let me boot it on startup (f12?) i dont have a ubuntu disk and need XP. I cannot get a driver for my wireless card so I need XP plus I want to play games CSS, modern warfare etc. I have no internet but will do If I get XP please help.

---

### Post by JigglyWiggly_ on 2009-11-21
What does this have to do anything with Ubuntu? Just go boot from cd.

---

### Post by R3V3RB on 2009-11-21
> **JigglyWiggly_ said:**
> What does this have to do anything with Ubuntu? Just go boot from cd.
 
 
It wont let me sorry Im not good at this side of computers what is the key to boot while it is loading

---

### Post by ashu. on 2009-11-21
> **JigglyWiggly_ said:**
> What does this have to do anything with Ubuntu? Just go boot from cd.

i dont understand why do u want to install ubuntu for Xp which has many problems.
still jus insret the disk-> restart the system ->choose boot from cdrom n install..or when u start u'll c manufacturer's screen like intel , mercury or etc etc there u'll c the keys to choose the boot menu press it n choose CDrom

---

### Post by jacobs444 on 2009-11-21
your bios is set to boot from HD first instead of cd. change these settings, and you will be able, though ubuntu has nothing to do with that part of the boot process.

---

### Post by DeMus on 2009-11-21
> **R3V3RB said:**
> I bought a PC that came with Ubuntu 9.04 intending on removing Ubuntu and installing XP i have a XP disk that works but Ubuntu wont read ti and wont let me boot it on startup (f12?) i dont have a ubuntu disk and need XP. I cannot get a driver for my wireless card so I need XP plus I want to play games CSS, modern warfare etc. I have no internet but will do If I get XP please help.

Put the Windows CD in the drive and reboot the computer
As soon as you see texts appear on screen look for anything that says:
... for Setup, or ... for BIOS
... will have a key mentioned.
Boot again and press that key to enter Setup (BIOS)
In BIOS look for the chapter Boot, enter it using your cursor keys
Make the CD drive the first item to boot from
Save the changes and let the pc reboot.
It will now reboot from the CD, saying:
If you want to boot from the CD press a key (different text probably, same content)
Now let Windows do it thing until you get to the point where it normally shows you the partitions you have. Since Windows is terrible in recognizing Linux partitions (there is nothing outside Windows) it will say something like Unrecognizable partitions.
Point a partition and choose to delete it, command is at the bottom of the screen.
Do this with all your partitions until you have one large free space area.
Now make a partition which is about 20GB (20000 MB)
Make a second partition on the left over space.
Point to the first partition and install Windows on it.

When connecting to the internet don't forget to install a good anti-virus program and all those other scanners a Windows system needs.

---

### Post by R3V3RB on 2009-11-21
> **ashu. said:**
> i dont understand why do u want to install ubuntu for Xp which has many problems.
still jus insret the disk-> restart the system ->choose boot from cdrom n install..
 
 
 
Its not working whenever I restart it just keeps loading Ubuntu never prompts me for anything. Is there a special key to push at a special time I keep pressing f12. It loads to fast for me to read the writting

---

### Post by JBAlaska on 2009-11-21
Is your xp disk original or a "copy", the disk may be bad or your cd drive may be bad.

Did you follow DeMus's instructions to enter the BIOS?

---

### Post by R3V3RB on 2009-11-21
> **JBAlaska said:**
> Is your xp disk original or a "copy", the disk may be bad or your cd drive may be bad.
 
Did you follow DeMus's instructions to enter the BIOS?
 
 
 
The disk Is real. The menu that comes up to tell me which key to press to go to bios on startup blinks in milliseconds and I dont get to see the key to press any ideas what to do

---

### Post by jacobs444 on 2009-11-21
goto manufacturers website, lookup bios keys and you will find your wisdom, these manufacturers like to hide that stuff these days.


usually del, f1-f12, or esc but check mfg's site

---

### Post by JBAlaska on 2009-11-21
The second you see the message about the key, **hit the "pause/break" key**, that will stop the boot cycle and let you read which key you need to press to enter the BIOS. 
That being said, it's either the "del", "F1" or "F2" most likely.

---

### Post by R3V3RB on 2009-11-21
Windows is Installing thanks everyone
Latter I will dualboot Ubuntu as I have lots of harddrive space
Thanks again

---

