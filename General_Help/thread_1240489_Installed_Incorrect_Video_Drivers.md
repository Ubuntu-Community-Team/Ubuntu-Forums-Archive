---
title: "Installed Incorrect Video Drivers"
date: 2009-08-14
forum: General Help
---

### Post by jon64 on 2009-08-14
Last night i put in a new ATI Radeon HD 2600XT into my ubuntu box and it ran fine. But i wanted to install the ATI drivers so all the graphics will run smoothly. So i installed the ATI drivers via the "Add/remove" the ubuntu start button and i guess that was the wrong set of drivers cause when i get the the login screen my monitor turns all black. I can see the POST and the ubuntu loading bar and thats about it.

I need help uninstalling the video drivers and replacing it with the correct drivers. Please help thanks! :popcorn:

---

### Post by soapBAR2 on 2009-08-14
Boot up your computer until your monitor turns black. Then, press CTRL+ALT+F1 to drop to Virtual Terminal 1 (JSKY, there's also CTRL+ALT+F2 for VT2, CTRL+ALT+F3 for VT3, etc). Then, type this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will reset your X-server to it's original install settings. The driver will still be there, but it will not be being used. Uninstall it at your leisure.

If you still want to install accelerated graphics, I recommend trying envy (it's a tool for installing graphics drivers, I know, seems a bit redundant to install a program to install a program, but there you go).

GNOME/XFCE (Ubuntu, Xubuntu) USERS:
```
sudo apt-get install envyng-core envynt-gtk 
```

KDE (Kubuntu) USERS:
```
sudo apt-get install envyng-core envyng-qt
```

---

### Post by aethex on 2009-08-14
Never tried this, but it might work in Safe mode.

If you're dual-booting, a Safe Mode (or Recovery Mode) entry will appear in the list of operating systems, courtesy of GRUB. My guess is that this will use the built-in drivers and disable most features so that you can uninstall the driver packages.

---

### Post by jon64 on 2009-08-14
I tried to get into Virtual Terminal as you said and i wasn't able to. It seems as if my ubuntu system isnt responding after the ubuntu loading screen. Is there anything i can do in ubuntu's recovery mode to fix this?

---

### Post by gradinaruvasile on 2009-08-14
> **jon64 said:**
> I tried to get into Virtual Terminal as you said and i wasn't able to. It seems as if my ubuntu system isnt responding after the ubuntu loading screen. Is there anything i can do in ubuntu's recovery mode to fix this?

Select recovery mode, then root prompt from the list
There type:

```
dpkg-reconfigure -phigh xserver-xorg

reboot

```

*Enter after each command

---

### Post by jon64 on 2009-08-14
I just tried that but still the same results. My system just halts and goes to a black screen.

---

### Post by gradinaruvasile on 2009-08-14
> **jon64 said:**
> I just tried that but still the same results. My system just halts and goes to a black screen.

Then boot in recovery mode/root prompt and type:

```
nano /etc/X11/xorg.conf
```

find the Section "Device"
insert the following line below the Identifier line

```
Driver "vesa"
```

press ctrl-o and then ctrl-x

reboot

---

### Post by jon64 on 2009-08-14
Computer still Halts. I have no idea what the hell is going on. The last thing i did was install the ATI drivers via add/remove. I dont understand why it would halt my system.

---

### Post by gradinaruvasile on 2009-08-14
Hmm. then maybe u should remove them. Log in the recovery console.

I think 

```
apt-get remove --purge fglrx*
```

should do it.

Then again

```
dpkg-reconfigure -phigh xserver-xorg
```

and

```
reboot
```

---

### Post by solitaire on 2009-08-14
If your machine is halting during the boot process you will need to use a LiveCD to boot the machine.

Then you can use [gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640")'s post #7 to edit the xorg.conf then reboot as normal.

Once it starts to can try the other suggestions to remove the offending drivers.... :)

---

### Post by soapBAR2 on 2009-08-14
> **jon64 said:**
> Computer still Halts. I have no idea what the hell is going on. The last thing i did was install the ATI drivers via add/remove. I dont understand why it would halt my system.

Your driver is pooched, and it's crashing the system. ATi is not the best for Linux, but you should still not have a halted system. Regardless, here's how you fix it

When you first turn on your computer, after the BIOS menu, from the grub menu, can you select the "recovery"/"single" mode? This will boot straight into terminal and bypass X (then do sudo dpkg-reconfigure -phigh xserver-xorg).

This is roughly you should see (the names and background images might be different, but it'll be a list of kernels/OSs):
[http://www.howtogeek.com/wp-content/uploads/2007/09/image55.png](http://www.howtogeek.com/wp-content/uploads/2007/09/image55.png)

If there's no "recovery" mode, then add "single" onto the end of the line that says "kernel". I believe this is "up/down until desired boot menu option is highlighted -> press "e" -> select the line beginning with "kernel" -> press "e" -> go to end of line -> type "single" -> press enter -> press "b". But this is from memory, so I could be wrong - follow the prompts.

---

### Post by jon64 on 2009-08-14
OMG it worked! wow thank you so much. I really appreciate your help. You saved me about 8 hours of transfering all my data from the hard drive to another hard drive lol. Thank you soooo much! :popcorn:

---

### Post by Corey Young on 2009-10-25
> **gradinaruvasile said:**
> Then boot in recovery mode/root prompt and type:

```
nano /etc/X11/xorg.conf
```find the Section "Device"
insert the following line below the Identifier line

```
Driver "vesa"
```press ctrl-o and then ctrl-x

reboot

Wow Wow Wow!  This worked for me.  Thanks for the advice.  This is amazing.  I like linux again.  One question....I am testing out Linux as a stable and secure alternative to Winblows.  Unfortunately, it failed to reboot about 1 day into the fun.  I have now fixed the problem thanks to Gradinaruvasile.  BUT, why did the problem happen?  Why would an OS considered to be so stable fail on me so soon?

---

