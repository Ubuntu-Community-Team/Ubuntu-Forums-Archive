---
title: "Disabling grub menu and going strait to Windows?"
date: 2009-10-11
forum: General Help
---

### Post by rwttaber on 2009-10-11
I am having problems with my laptop. It will not charge. The computer is still warranted so I'm thinking of calling tech-support and have them solve the problem. Since there is a chance of me having to send it in I was wondering how to disable the grub menu and have it go strait to windows, without hurting my ubuntu installation.

By the way I have less then an hour remaining on battery :(

rwt

---

### Post by kestrel1 on 2009-10-11
From what I remember if you can boot to DOS & type:
fixmbr
That may do it.
If the laptop isn't charging have you checked that the mains power adapter is functioning correctly? Make sure that the mains lead is correctly inserted in the adapter & if it has a light on the adapter check that is on. Also switch off the machine & remove the battery & re-insert it. Some times this helps believe or not.

---

### Post by louieb on 2009-10-11
**See lswest's and bodhi.zazen's thread**, [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB ]("http://ubuntuforums.org/showthread.php?t=740221")
lswest links you to a site where you can download your very own Windows Vista Recovery CD if you don't have one, (if your Windows system is genuine and validated), and give you the commands for setting your hard disk's MBR to boot Windows and restore the Windows boot sector too, for Vista and XP.
lswest also tells you how to restore GRUB.
bodhi.zazen chimes in and tells us how to restore Windows boot loaders from Linux, (without the need for a large download).

or pull the hard drive before sending it in. Tell them it contains sensitive data. They will just use a stock drive during the repair.

---

### Post by rwttaber on 2009-10-11
So the only way to go strait to vista is to restore the vista boot loader :( ? Oh well, I will take your advice louieb and do lswest tutorial.

---

### Post by louieb on 2009-10-11
Another way is to alter /boot/grub/menu.lst. three things
change the default boot to Vista
change the line ```
#hiddenmenu
``` to ```
hiddenmenu
```
and change the timeout line to ```
timeout 0
```
The problem with doing it this is getting the GRUB menu to Display (you have to press <esc> at just the right time during boot). 

 Either way is going to take about the same amount of time.

---

### Post by ubun_two on 2009-10-11
> **louieb said:**
> Another way is to alter /boot/grub/menu.lst. three things
change the default boot to Vista
change the line ```
#hiddenmenu
``` to ```
hiddenmenu
```
and change the timeout line to ```
timeout 0
```
The problem with doing it this is getting the GRUB menu to Display (you have to press <esc> at just the right time during boot). 

 Either way is going to take about the same amount of time.
Either way, I think the grub menu can be brought back using Ubuntu Live CD.

---

