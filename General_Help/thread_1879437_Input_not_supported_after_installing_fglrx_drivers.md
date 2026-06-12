---
title: "Input not supported after installing fglrx drivers"
date: 2011-11-11
forum: General Help
---

### Post by paulalmarinez on 2011-11-11
Help! I am a noob when it comes to linux.

Well my problem is that, when i boot my pc. after the loading screen of ubuntu, it just shows me "Input Not Supported". While the monitor only shows this, i hear the login tune so i think that means that ubunutu did run but my monitor cant show me the desktop.  This happened after i installed the drivers for my video card. Anyone know how i can fix this? after the booting screen i cant see anymore, only the Input Not Supported message moving in my screen.

Help?

My Video Card is an ATI Radeon HD 3650 pci-e card. 
I installed the 11.10 ubuntu.

Any help would be very much appreciated! Thanks!:)

---

### Post by BillyBoa on 2011-11-11
You can download the latest ATI drivers to see if the situation is bettering.

[http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml](http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml)

Download the driver and then right click to make the file executable.

Then move it to Home directory

from a terminal

```
sudo ./the name of the driver
```

follow the instructions

---

### Post by paulalmarinez on 2011-11-11
Ohh.. so i need to reinstall the whole ubuntu again for it to rollback? or is there a way to enter ubuntu on like a safe mode or something?

---

### Post by BillyBoa on 2011-11-11
Well if you feel that installing the new drivers is complicated, then try to unistall the drivers you installed through the application-Additional Drivers. Look if the situation is better without those drivers.

---

### Post by paulalmarinez on 2011-11-11
Well the thing is sir i cant see my desktop(if it is whats it is called in ubuntu) anymore. Before i can see the desktop, the Input Not Supported the only thing being shown in my screen so i cant do anything anymore.

---

### Post by BillyBoa on 2011-11-11
Ok understood

Restart the computer and choose in the start up screen to start on (recovery mode)
Find the terminal or drop to a terminal by hitting CTRL + ALT + F1 and type

```
sudo su
``` put your password
```
cd /home/**[COLOR="Red"]your logon name[/COLOR]**
```
```
rm -r .gnome .gnome2 .gconf .gconfd
```

---

### Post by paulalmarinez on 2011-11-11
ohh ill go check for the recovery mode. but i think i havent that somewhere.. imma go check that! Thank you very much kind sir!

---

### Post by paulalmarinez on 2011-11-14
UP^^

I tried the fix bro but cant get it though.. it says it could not find the file.. :(

i triend configuring the xrandr setting but it say "Cannot show display" or something like that. Any help?

---

### Post by BillyBoa on 2011-11-14
Yeap, I fell in the same hole!

I had the same problem few hours ago and nothing.

I'm just in the middle of a fresh installation.

Might be a bug.

---

### Post by paulalmarinez on 2011-11-14
ohh.. huhuhuhu but i havent backed up yet... huhuhuhu.. 

do you know how to backup through terminal? how can i transfer files to an eternal drive?

---

### Post by BillyBoa on 2011-11-14
Use an installation (Live) CD.

Boot from the CD.

From nautilus left pane chose the files you need to backup and copy them.

If you have any problem (some files are not permitted to copy and so on) use:

```
sudo nautilus
```

from this root nautilus copy the files you have to salvage (the problem is that you later on have to change ownership to the files but this is a minor problem)

When you reinstall the system, use a separate partition for / (for your system files about 6G) and another one for /home

When you have similar problem you choose to format the / directory but not the /home in which is installed your personal files and many configurations you made.

---

### Post by paulalmarinez on 2011-11-14
i see! well thanks for the good advice my friend! :)

---

