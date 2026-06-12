---
title: "Have to type startx after login to get to GUI desktop"
date: 2011-03-08
forum: General Help
---

### Post by Rikeshar on 2011-03-08
I've looked around for a bit and can't find the exact answer to the problem I'm having. 

Whenever I load up my computer, Ubuntu comes up with a command line asking for my user name and password. I can type all that in, and get into the system, but it's still in the command line. If I type startx, it will then load the GUI desktop just fine. Is there any particular reason it wont' boot straight into a GUI login screen?

I originally had Ubuntu dual booted with Windows 7, and was having this problem. When I installed Ubuntu fresh on an external hdd, the issue went away. However, I recently formatted the hdd and re-installed Ubuntu and now it's doing this again. 

Any help would be appreciated!

---

### Post by lithopsian on 2011-03-08
Installed or configured wrong.  GDM should start X for you, it is a standard part of the installation.  Would need a lot more information to diagnose why it isn't working.  See if you are getting an X log file when you boot and if it contains an error.

---

### Post by Rikeshar on 2011-03-08
Hello Lithopsian,

I checked the Xorg log but didn't see any errors. Is there somewhere else I should be looking?

What's happening exactly, is that I'll power the computer on. The screen stays black for 30 secs to a minute, then it comes up asking for my login. Right above this (on this reboot at least) it says:

[22.656024] tpm_tis 00:0b: tpm_transmit: tpm_send: error 4294967234

When I log in through this command line (which is in tty1, which I gather is just one of the virtual terminals) the screen goes black for a few more seconds, and then comes to a GUI login screen which shows my screen name. Next to the screen name it says "currently logged in." I click this, enter my password, and then it asks me 2 or 3 times for my keyring password, since it wasn't activated when I logged in.

What other information might I provide that would be useful?

---

### Post by vivek.pandey on 2011-03-08
have you checked grub?
if not please post here output of
sudo cat/etc/default/grub

---

### Post by Rikeshar on 2011-03-08
Well, I had some difficulties with grub recently, and so I've updated it to grub2 (as far as I know). 

Here's the output of /etc/default/grub though:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=5
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Rikeshar on 2011-03-09
Anyone have any ideas?

---

### Post by watupgroupie on 2011-03-09
I had this problem after upgrading to 10.10. I remember solving it while trying to solve a problem with Ubuntu Tweak. I think it had to do with setting the system to automatic login.

Edit: Nevermind, turn off automatic login. 
1. sudo gedit /etc/gdm/custom.conf
2. change AutomaticLoginEnable to false
3. Reboot

---

### Post by Rikeshar on 2011-03-10
Hm... I tried changing my user setting so that it wouldn't ask for password on login, but this didn't change anything at all. And, when I went to try to edit the /etc/gdm/custom.conf it came up empty. I navigated to that folder in nautilus and there is no custom.conf, so I can't change the setting. Would this have something to do with the issue? Is there a way remove gdm and install it clean? Would that work? I've tried doing

sudo apt-get remove gdm

and then

sudo apt-get install gdm

with no change. Same with removing and installing ubuntu-desktop.

**EDIT**

I'm not sure if this is relevant, but I just noticed that in System > Preferences > Monitors the system cannot recognise my monitor. I know that it did before I reinstalled Ubuntu, and before I started having these problems. I checked the Xorg.0.log and it mentions: 

```

(WW) Falling back to old probe method for fglrx
[   623.734] (II) Loading PCS database from /etc/ati/amdpcsdb
[   623.735] (--) Assigning device section with no busID to primary device
[   623.735] (--) Chipset Supported AMD Graphics Processor (0x94C1) found
[   623.735] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[   623.735] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[   623.735] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
[   623.735] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[   623.735] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[   623.736] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[   623.736] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[   623.736] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:3) found
[   623.736] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:4) found
[   623.736] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:5) found
[   623.736] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[   623.736] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[   623.736] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[   623.736] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[   623.736] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
```

and 

```
WW) fglrx(0): board is an unknown third party board, chipset is supported
```

I'm using a Lenovo display and an ATI graphics card. The additional drivers program lets me activate an "ATI/AMD proprietary FGLRX graphics driver."  I've just deactivated it. About to restart to see if that helps at all.

---

### Post by Rikeshar on 2011-03-10
VICTORY!!! 

After deactivating the restricted driver ubuntu wanted me to install, I have my gdm back, and when doing CTRL+ALT+F1 etc for terminals, the font is not obnoxiously large like it has been. 

Marking this one as solved, hopefully it'll be useful to others. :D

---

