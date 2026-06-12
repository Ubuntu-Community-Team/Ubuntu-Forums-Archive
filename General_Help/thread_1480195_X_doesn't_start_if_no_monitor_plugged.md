---
title: "X doesn't start if no monitor plugged"
date: 2010-05-11
forum: General Help
---

### Post by galehar on 2010-05-11
The computer is used as a server and I connect remotely on it with VNC. It has no monitor. It was working fine until I upgraded to Lucid. Now, it only works with a basic vesa driver (800x600 max res). The log says:

NVIDIA(0): No display devices found for this X screen.
Screen(s) found, but none have a usable configuration.

If I plug a monitor, it work fines. Is there a way to disable monitor detection?

---

### Post by kafkaz on 2010-05-18
I have the same problem, only the difference - I use FreeNX instead of VNC. I was hunting for the solution two weeks, but until now I found nothing. 
I found only NVidia note about new realize:

*Now, the NVIDIA X driver will not automatically pretend that any CRTs are connected. If the X driver does not detect any connected display devices, the X server will fail to start.*

source:
[http://ubuntuforums.org/showthread.php?t=990978&page=111]("http://ubuntuforums.org/showthread.php?t=990978&page=111")

I have good resolution, but video card's fan is very noisy. 
Any NVIDIA guru here?:)

---

### Post by kafkaz on 2010-05-19
I have a solution.
Add this line to the Device section of xorg.conf:
Option "ConnectedMonitor" "CRT"

For example:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "ConnectedMonitor" "CRT"
EndSection


Source:
[http://www.nvnews.net/vbulletin/showthread.php?p=2253943&posted=1#post2253943]("http://www.nvnews.net/vbulletin/showthread.php?p=2253943&posted=1#post2253943")

---

### Post by mb_webguy on 2010-05-19
I had this problem recently in setting up a headless media server which I wanted to be able to connect to using VNC through ssh.

The problem is due to KMS (kernel-mode-setting), which detects the attached monitor on startup and configures your output settings automatically -- which is nice if you're running a normal desktop, since if you get a new monitor you don't have to do any special setup.  But it's a pain if you're trying to set up a headless system, and won't have a monitor attached, since with KMS on, Ubuntu boots into a safe graphics mode with a confirmation prompt (which you of course can't see, since you don't have a monitor attached).

The solution is fairly simple, and just involves a minor edit to GRUB, as described in the [Lucid release notes]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture").  For GRUB 2, edit /etc/default/grub and add nomodeset to GRUB_CMDLINE_LINUX, then run sudo update-grub.  For GRUB 1, edit /boot/grub/menu.lst and add nomodeset to the line beginning with # kopt=, then run sudo update-grub.  You might have to reboot once with a monitor attached (I can't remember if I had to do so or not), but after that, Ubuntu will boot normally into a graphical environment without the necessity of an attached monitor.

---

### Post by Groodles on 2010-05-19
[http://ubuntuforums.org/showthread.php?p=9235045#post9235045](http://ubuntuforums.org/showthread.php?p=9235045#post9235045)

---

### Post by SFSDCris on 2010-05-24
How do you get around situations in which Ubuntu requires input during the boot process?

I have no keyboard or monitor attached to my media server.

I currently have a situation where if there is a problem, ubuntu stops on boot and asks which system (recovery or standard) I want to run. 

Secondly, if there is a disk problem, Ubuntu requires I run a disk check from command line, and to hit 'y' a bunch of times to approve attempted fixes. 

For a headless, keyboardless media server this is impossible. 

Auto-rebooting after a power failure, auto-attempting to fix disk problems needs to be an option. Is there a way to do this?

---

### Post by Groodles on 2010-06-17
> **SFSDCris said:**
> How do you get around situations in which Ubuntu requires input during the boot process?

I have no keyboard or monitor attached to my media server.

I currently have a situation where if there is a problem, ubuntu stops on boot and asks which system (recovery or standard) I want to run. 

Secondly, if there is a disk problem, Ubuntu requires I run a disk check from command line, and to hit 'y' a bunch of times to approve attempted fixes. 

For a headless, keyboardless media server this is impossible. 

Auto-rebooting after a power failure, auto-attempting to fix disk problems needs to be an option. Is there a way to do this?

I've not found a way to do that yet.

---

