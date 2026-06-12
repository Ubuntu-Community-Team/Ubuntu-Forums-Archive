---
title: "Odd installation problem"
date: 2011-04-12
forum: General Help
---

### Post by Robing Goodfellow on 2011-04-12
I convinced a coworker to try ubuntu.  He had problems with the installation which I determined to be lack of swap, so I told him to bring me the laptop (Toshiba satellite P505b 64 bit) and I'd do the install for him.  All went well until I restarted after the install (did NOT install updates or third party stuff during install, bad internet connection at work, figured he could do that at home).

It goes through the log-in screen fine, into the ubuntu purple swirl desktop background, but no panel, tray, nothing.  Just wall paper.  Any ideas?

regards, Richard

---

### Post by seawolf167 on 2011-04-12
[LIST]
[*]Are you able to switch to the first console? [CTRL][ALT][F1]
[*]Does/did the LiveCD work?
[*]Did you MD5Sum the download to ensure that it was correct?
[/LIST]

---

### Post by Robing Goodfellow on 2011-04-12
Nope, you got it Seawolf, thanks.  Bad LiveCD. Thanks

---

### Post by seawolf167 on 2011-04-12
Glad it was an easy fix! :)

---

### Post by Robing Goodfellow on 2011-04-13
I thought we had this one solved.  Just finished a fresh install dual boot on this machine with a disk I know to be good as I have used it for several other installs including my own machine.  Same thing, log into Maverick and just get background.  

[CTRL][ALT][F1] takes me into terminal just fine.   

LiveCD doesn't work.

Is it possible for a machine to be incompatible with Ubuntu????

curiouser and curiouser was, Richard

---

### Post by seawolf167 on 2011-04-13
If you turn on your speakers and turn the volume up, when you boot the machine and let it sit there for a minute do you hear the "drum beats" that signifies that Ubuntu got to the login screen?

---

### Post by Robing Goodfellow on 2011-04-13
Yes.  I get the drumbeat at login, get the etheral "AAAHHHHHHHHHHhhhhhhhhhhhh" right after that as it loads up, background loads fine.  No panel, no tray.  Cursor moves fine with touchpad.  I didn't think to do a right click on desktop to see what happens, I'll go try that now.

regards, Richard

---

### Post by Robing Goodfellow on 2011-04-13
Right click, left click, nuffin. :(

---

### Post by seawolf167 on 2011-04-13
So it sounds like your machine is booting ok, but you have a graphics problem then. The next thing I'd try (especially since you said you can enter the first console) is to reconfigure x-server-xorg with the following commands (after entering the console with [CTRL][ALT][F1])

Backup the current configuration

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```Reconfigure

```
sudo dpkg-reconfigure xserver-xorg
```Follow the prompts and select the options as best you can

If it doesn't start after the reconfigure, type in the following commands to attempt to start the xserver &/or gdm

```
startx
sudo service gdm restart
```

---

### Post by kiyop on 2011-04-13
How about pressing ALT+F2 or ALT+F1?
If you can open "gnome-terminal",
```
gconftool --recursive-unset /apps/panel
killall gnome-panel
```may help.

Added at 4/13 22:44 in Japan:
[#9]("http://ubuntuforums.org/showthread.php?p=10671912#post10671912") may be better.
Only the portion of desktop (middle in the height) may be displayed.

---

### Post by Robing Goodfellow on 2011-04-13
Nope, tried both suggestions, no joy, but thanks for all the help.  I'm beginning to think its a hardware issue.  I am now told that this laptop was "found at the dump" missing a hard drive.  Appears to be in good shape, but why would anyone discard a relatively new laptop?  I'm betting it's either a hardware compatibility issue with Linux or there was a good reason the laptop was discarded.  Can't figure anything else that makes sense.  Any disagreement?

regards, Richard

---

### Post by kiyop on 2011-04-14
Some kernel options may have to be added to display correctly. I am not sure.
If your boot loader is grub2, you can display grub2 menu by pressing shift key at booting and you can change kernel options, by pressing E key. You can boot with modified kernel options by pressing CTRL+X.

Candidates for kernel options:

xforcevesa
nomodeset
all_generic_ide
irqpoll
acpi=off
nolapic
vga=791 
# 791 should be modified in accordance with your display resolution

---

