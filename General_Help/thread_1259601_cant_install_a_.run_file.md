---
title: "cant install a .run file"
date: 2009-09-06
forum: General Help
---

### Post by glenuk on 2009-09-06
hey i'm trying to install ati graphics drivers for linux its a .run file i use these instructions but i get stuck
1. Open a terminal. In Gnome the terminal is found in Applications>Accessories>Terminal.
2. Navigate to the directory of the .run file. For this example, I have mine on the desktop so I would type in "cd ~/Desktop" and press enter.
3. Type "chmod +x example.run" (press enter).
4. Now type "./example.run", press enter, and the installer will run.
it goes through the uncompressing process and gets to where it says 

 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.4 and later releases 

when a message box pops up saying "you need to run this installer as the super user
can anyone help me with this plz 
thanks in advance
glen

---

### Post by NoaHall on 2009-09-06
use "sudo ./example.run"

---

### Post by glenuk on 2009-09-06
kool thank you that worked

---

### Post by glenuk on 2009-09-06
sorry new problem i installed the software but when i go to launch the software i get another message box saying:
there was a problem initializing catalyst control center linux edition. it could be caused by the following.
no ati graphics driver is installed, or the ati driver is not functioning properly.
please install the ati driver appropriate for your ati hardware, or configure using aticonfig
how can i fix this problem please 
thnx in advance 
glen

---

### Post by makariolewis on 2009-09-06
What type of graphics card do you have? Are you sure that it's an ATI card? If so, what model is it?

---

### Post by glenuk on 2009-09-06
it an ati radeon x1650 pro

---

### Post by makariolewis on 2009-09-06
Try rebooting if you haven't. If that doesn't work, try running 'sudo aticonfig --initial' and see if that does the trick.

---

### Post by glenuk on 2009-09-06
i rebooted now it goes funny after the splash screen & can access the log in screen or my desktop i need help
thanx 
glen

---

### Post by TheFuzz4 on 2009-09-06
Instead of downloading and installing from ATI try installing envy do a 
sudo apt-get install envyng-qt
Then drop down to a command line and run
sudo envyng -t for the text instaler
It will ask you what type ATI or NVIDIA just punch in the number corresponding to it
Then it will show you which driver is compatible with your card with two + signs just select that number and let it install. 
I use envy everytime I do a install and it always works like a champ.
After your install is complete do a reboot and you'll be gold.

---

### Post by makariolewis on 2009-09-06
If you can't access your desktop, here's how to fix it:

1. Reboot your computer, and hit escape when given the option in GRUB.
2. Boot into Ubuntu's recovery mode. You should be able to repair your graphics in there by resetting everything back to normal.

---

### Post by glenuk on 2009-09-06
but since i rebooted after installing the software i cant get to my desktop to do anything the screen flashes & the graphics look like when a game or something crashes & the screen flashes i'm having to use the live disk to write this is there anyway round this without reinstalling windows??
thanx 
glen

---

### Post by glenuk on 2009-09-06
> **makariolewis said:**
> If you can't access your desktop, here's how to fix it:

1. Reboot your computer, and hit escape when given the option in GRUB.
2. Boot into Ubuntu's recovery mode. You should be able to repair your graphics in there by resetting everything back to normal.

i've tried that but it hasnt helped 
thanx 
glen

---

### Post by gradinaruvasile on 2009-09-06
> **glenuk said:**
> i've tried that but it hasnt helped 
thanx 
glen

Hmmm... U should select the recovery mode from the boot list, then on the next list select boot prompt. Log in (in text mode) and type:

```
dpkg-reconfigure -phigh xserver-xorg
```

Then

```
reboot
```

U will have the default configuration back. 

What version of Ubuntu do u use?
If u use the current version (9.04) ur card is not supported anymore by the Ati driver u wanted to install.
If u have 8.04 or 8.10 the driver should work.

---

### Post by TheFuzz4 on 2009-09-06
Also if you can't get back to a desktop after a reboot do a ctrl + alt then any F1-F6 and that will drop down to a terminal for you and at least you can work from the command line.
Have you tried using envy yet?  I would really give envy a shot.

---

### Post by glenuk on 2009-09-06
i'm still new to linux and am not used to the command line yet & i havent heard of envy before
thanx 
glen

---

### Post by glenuk on 2009-09-06
> **gradinaruvasile said:**
> Hmmm... U should select the recovery mode from the boot list, then on the next list select boot prompt. Log in (in text mode) and type:

```
dpkg-reconfigure -phigh xserver-xorg
```Then

```
reboot
```U will have the default configuration back. 

What version of Ubuntu do u use?
If u use the current version (9.04) ur card is not supported anymore by the Ati driver u wanted to install.
If u have 8.04 or 8.10 the driver should work.

i've tried this and when it stops i get this message:
"xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/x11/xorg.config.2009090720937"
and when i reboot the same thing happens & nothing has changed
thanx 
glen

---

### Post by glenuk on 2009-09-07
i've tried whats advised above a few times now with no change is there anyway to sort this out with out reinstalling 
thanx
glen

---

### Post by oldos2er on 2009-09-07
You could try reinstalling the open source drivers. In recovery mode, run **apt-get install xserver-xorg-video-ati**

---

### Post by glenuk on 2009-09-07
> **oldos2er said:**
> You could try reinstalling the open source drivers. In recovery mode, run **apt-get install xserver-xorg-video-ati**

kool i'll try that now thnx if i want to get rid of it completely how would i go about doing that please?
thanx for your help
glen

---

### Post by glenuk on 2009-09-07
> **oldos2er said:**
> You could try reinstalling the open source drivers. In recovery mode, run **apt-get install xserver-xorg-video-ati**

i've tried this but theres been no change 
thanx 
glen

---

### Post by glenuk on 2009-09-07
have just tried doing the apt-get install xserver-xorg-video-ati again & noticed a massage that read: "xsever-xorg-video-ati is already the newest version."
is there any way to revert it back or restore the install to a time before i messed it up using the command line
thnx 
glen

---

### Post by glenuk on 2009-09-07
i got it all sorted now. 
thank you all for your time & help
glen

---

### Post by Yitzach on 2009-12-31
The step between numbers 21 and 22 is reboot. Had figure that out myself.

---

