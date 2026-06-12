---
title: "Multiple problems with Lucid"
date: 2010-05-01
forum: General Help
---

### Post by Umang on 2010-05-01
Hi,
I upgraded to Lucid yesterday and I'm having some problems.

Background: I'm running a really old machine. No graphics card, therefore no compiz, etc. I did a fresh install (I had a separate /home partition which wasn't formatted. Only / was formatted.)

**1. gnome-panel doesn't show at all -- most major**
When I login after a restart, gnome-panel doesn't show at all. I have to killall gnome-panel to get something to display. Before killing gnome-panel, there seems to be some space allocated for the panel (that is momentarily lost after killing the old panel and before the new gnome-panel takes over). Alt+F1 works, the desktop too works. If I use tty1 to delete .gconfd, .gconf, .gnome2 and .gnome2_private and login after that, I see a gnome-panel like I'm supposed to. I restart the computer and it's back to not working. I don't want to killall gnome-panel everytime I login. It doesn't seem to me that this is related to lp:508452 that I am affected by also. (I have, BTW, tried reinstalling all gnome-panel and applets related packages, which hasn't helped)

**2. Boot experience got far worse + flickering during boot and login**
I'm suspecting this isn't the case for those with graphics cards, but this is what happens anyway:
After I enter Ubuntu from GRUB, I get the cursor blinking on the top-left of the screen like in all previous releases (can't we get rid of that altogether?). Now, unlike in Karmic and before, the cursor stays for 10 to 15 seconds. (Earlier it was 2 to 3 seconds). The screen flickers - the screen flashes with green and orange colors for a second before the new splash screen appears - for two seconds (by which time two of the circles are filled). The screen flashes again (black this time) and then the splash screen returns (with all the circles filled). After some more flashes of black, I get the login screen (gdm).

After logging in, I get see the mouse, wallpaper and around ten stretched images of the icons on my desktop. All this under a set of close black lines (as if to dull the screen). There is an ugly box that doesn't have these lines at all around the mouse pointer. The screen fixes itself after five or six seconds - without the panel.

Overall, the whole boot and login experience just go uglier.

**3. [SOLVED]My terminal auto-complete broke**
I don't seem to be able to auto-complete anything after the first statement in the terminal. e.g. `man pytho` + TAB + TAB + TAB doesn't give me a list of man pages beginning with pytho nor does it auto-complete to python. Similarly I cannot auto-complete package names with `sudo apt-get install` neither with apt-cache policy, etc. I suspect this is a minor problem caused by something else though. **(I solved this by creating a new user and copying the new user's .bashrc)**

Any help with this would be much appreciated,

Thanks in advance

---

### Post by Umang on 2010-05-01
It seems to be getting worse now. I'm having to kill both gnome-panel and nautilus now. I just tried this on a freshly created account. No desktop, no panels. I Ctrl+Alt+T and then kill both to get the anything to show up.

This isn't the first unpleasant experience. In fact, even since I first installed Gutsy, Hardy and Jaunty have been the only upgrades to have no major problems and only a few minor problems. Here's the thread from my Karmic upgrade: [http://ubuntuforums.org/showthread.php?p=8232548](http://ubuntuforums.org/showthread.php?p=8232548). Hardy was the only version that didn't have a frantically flickering screen on boot.

With this upgrade, I my respect for Ubuntu is slowly dimishing.

---

### Post by strange_cathect on 2010-05-01
NVIDIA graphics card?

---

### Post by Umang on 2010-05-01
No. No graphics card at all. :p To reflect that, I chose "ancient" as the computer name this time instead of "home-ubuntu". Maybe the CPU didn't like that and messed the installation up. ;)

Really, it's a torture trying keep this thing running. I really need it to hang in a year or two more. So if I get Lucid to work, I'm not upgrading this till I get a new machine (hopefully before 12.04).

---

### Post by rnerwein on 2010-05-01
> **Umang said:**
> It seems to be getting worse now. I'm having to kill both gnome-panel and nautilus now. I just tried this on a freshly created account. No desktop, no panels. I Ctrl+Alt+T and then kill both to get the anything to show up.

This isn't the first unpleasant experience. In fact, even since I first installed Gutsy, Hardy and Jaunty have been the only upgrades to have no major problems and only a few minor problems. Here's the thread from my Karmic upgrade: [http://ubuntuforums.org/showthread.php?p=8232548](http://ubuntuforums.org/showthread.php?p=8232548). Hardy was the only version that didn't have a frantically flickering screen on boot.

With this upgrade, I my respect for Ubuntu is slowly dimishing.

hi
no graphic card -> gnome, panel etc. :confused: :confused: :confused: :confused:
tell me how you manage that
ciao

---

### Post by Hydrokys on 2010-05-01
As for the gnome panel not showing up -that happened to me when i disabled visual assistance from the startup application preferences. don't know about you but enabling it solved MY issues.

---

### Post by Umang on 2010-05-01
About the graphics card: I'm sorry. I thought it was the same as something else (probably 3D accelerator or whatever that is. I basically cannot run compiz or anything else that required acceleration). Forgive my poor knowledge of hardware.

```
$ sudo lspci |more
[sudo] password for umang: 
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory 
Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Cont
roller (CGC) (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 11)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 11)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 11)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio C
ontroller (rev 11)
01:00.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev
 01)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139
C+ (rev 10)
```

Also, I haven't disabled Visual assistance.

---

### Post by Umang on 2010-05-01
Oh and something interesting seems to be happening. I can now get the gnome-panel properly about once in three logins (after a restart). But nautilus still doesn't load on any occasion unless I kill it first.

---

### Post by Umang on 2010-05-03
I reinstalled many gnome and x related packages and there seems to be some improvements now with the gnome-panel/nautilus issue. All the other problems I mentioned have separate threads of their own. I'll try to fix them. I am also considering antiX right now, but if all this gets fixed, I'm not going to bother installing any other OS until we get a new computer.

---

### Post by absolutezero1287 on 2010-05-03
> **Umang said:**
> 
```
$ sudo lspci |more
[sudo] password for umang: 
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory 
Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Cont
roller (CGC) (rev 04)

```

I've been having the same issue. The flickering screen during boot and on top of that my system randomly crashes. It seems that we have the same ancient graphics card. Perhaps we're both suffering from the same issue? Post the output of the following command: cat /var/log/Xorg.0.log | grep -i "(WW)" and do the same for Xorg.0.log.old.

```

me@satori:/var/log# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

me@satori:/var/log# cat Xorg.0.log.old | grep -i "(WW)"
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000000 to 0x00000207
(WW) intel(0): PIPEASTAT before: status:
(WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): ESR is 0x00000001, instruction error
(WW) intel(0): Existing errors found in hardware state.

```

I think the answer to the problem is rolling back the graphics driver. The latest intel gfx driver has always given me issues.

---

### Post by Umang on 2010-05-03
```

umang@ancient:~$ cat /var/log/Xorg.0.log | grep -i "(WW)"
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
umang@ancient:~$ cat /var/log/Xorg.0.log.old | grep -i "(WW)"
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)

```What can we rollback to?

---

### Post by absolutezero1287 on 2010-05-03
> **Umang said:**
> What can we rollback to?

Well, if I recall correctly the more stable version of the intel gfx driver is 2.7. If you do a "dpkg -l | intel" you'll get a list of all currently installed packages with the word "intel" in them. You should get one that says something along the lines of: xserver-xorg-video-intel 2:2.9.1-3ubuntu

I looked it up at packages.ubuntu.com and found versions 2.2-2.6 and 2.9 but not 2.7.

Edit: Found the package [here.]("https://launchpad.net/ubuntu/karmic/i386/xserver-xorg-video-intel/2:2.7.99.901+git20090702.74227141-0ubuntu1")

---

### Post by absolutezero1287 on 2010-05-03
Update: The 2.7 version conflicts with xserver-xorg-core. They both provide a package called xserver-xorg-video-5. The only way I can think of fixing this issue is to rebuild the .deb or somehow tell dpkg not to install the old version of xserver-xorg-video-5. However, I have no idea how to do any of these things.

---

### Post by Umang on 2010-05-03
> **absolutezero1287 said:**
> Well, if I recall correctly the more stable version of the intel gfx driver is 2.7. If you do a "dpkg -l | intel" you'll get a list of all currently installed packages with the word "intel" in them. You should get one that says something along the lines of: xserver-xorg-video-intel 2:2.9.1-3ubuntu

I looked it up at packages.ubuntu.com and found versions 2.2-2.6 and 2.9 but not 2.7.Yes, I knew which package to look in (in fact that was one of the reinstalled packages). I don't think there is any lucid package for a previous version available in the lucid repos since this is the version in lucid not in the updates repo.

And... I had to `killall nautilus gnome-panel` again just now. I don't seem to be headed anywhere now. :confused:

EDIT: Sorry, just saw your newer replies. I don't really know about how xserver works. So I don't know whether having conflicting versions of different xserver packages is a good idea.

---

