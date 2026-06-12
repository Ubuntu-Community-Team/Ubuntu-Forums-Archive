---
title: "desktop computer boots into text mode after nvidia drivers installed"
date: 2011-01-12
forum: General Help
---

### Post by FraggerMan on 2011-01-12
Hey guys, sort of a noob to ubuntu here, but not a noob to general computing. After installing ubuntu 64 bit, I installed all my updates and installed the current nvidia driver for my 9800 GTX+ from the additional drivers page. After restarting my computer, ubuntu boots into text mode. I used google and found out a couple of commands like 

sudo dpkg -reconfigure -phigh xserver-xorg - does nothing
after i hit control+alt+f7 it hangs on checking battery state with NO ok to the right of it.
after running sudo apt-get --purge remove nvidia -current and restarting the computer,
the boot hangs on the ubuntu screen everytime.

Thanks for reading guys, and any or all help would be highly appreciated.

My specs are:
Core i7 860
4 GB of ram
Nvidia 9800 GTX+

---

### Post by FraggerMan on 2011-01-12
bump, sorry but I really need help!

---

### Post by Verbeck on 2011-01-12
try setting the nomodeset parameter on boot
from grub, press 'E' when the ubuntu entry is selected and replace *quiet splas*h with *nomodeset . * then press ctrl+X to boot

and if grub is hidden by default, hold down 'shift' while the computer is booting up

---

### Post by FraggerMan on 2011-01-12
I use grub to dual boot with windows 7, but I am positive the problem lies with nvidia-current.

---

### Post by Muster Mark on 2011-01-12
Let me first say that I am no expert at all.  My only experience is getting my own computer to work.

The open source nVidia drivers are not incredibly reliable with all cards.  I think you need to disable them in the Grub even if you have installed the proprietary ones. This is just something to try, but perhaps the following will help (it worked for me with my nVidia nvs3100M).

When you get to the grub menu, press the 'e' key to edit the boot command, and go down to the "kernel" line. Add "nouveau.modeset=0" to the end of the line containing "quiet splash", then press Ctrl+x to boot.

Good luck!

---

### Post by FraggerMan on 2011-01-12
Thanks alot Mark! I will try this.

---

### Post by FraggerMan on 2011-01-12
That ended up not working :(

---

### Post by FraggerMan on 2011-01-13
Bump! Really need help guys. Thanks

---

### Post by FraggerMan on 2011-01-13
bump

---

### Post by FraggerMan on 2011-01-16
bump guys

---

