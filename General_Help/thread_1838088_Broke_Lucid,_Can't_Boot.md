---
title: "Broke Lucid, Can't Boot"
date: 2011-09-02
forum: General Help
---

### Post by timnugent on 2011-09-02
Hello All,

I've been happily running Lucid Lynx 10.04 since the late summer of 2010. A minor irritation to me was that the splash screen logo ('Ubuntu') became pixelated after I installed Lucid. Last night I found the following web site:

[www.Ubuntugeek.com](www.Ubuntugeek.com)

I found the following article to address this issue: "Known Ubuntu 10.04(Lucid Lynx) issues/bugs with workarounds"

Under item number six in this list, the following was presented:

How to Fix the Big and Ugly Plymouth Logo in Ubuntu 10.04

Problem

The logo looks fine when you install Ubuntu, but, after you install the

proprietary Nvidia and ATI video drivers, the logo gets bigger and ugly!

Below, we provide two fixes for this issue: the first one will fix the resolution of

the Ubuntu logo, pretty much like it was when you installed Ubuntu; and the

second one will remove the logo, showing only a dark screen until the login

manager appears.


Workaround

Step 1: Hit the ALT+F2 key combination, paste the following command and

check the “Run in terminal” option:

sudo apt-get install v86d

Step 2: Hit the ALT+F2 key combination, paste the following command and

check the “Run in terminal” option:

gksu gedit /etc/default/grub

...enter your password when asked and hit the Enter key.

- Replace the following line (line number 9):

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”

with this one:

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash nomodeset

video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap”

- Replace the following line (line number 18):

#GRUB_GFXMODE=640×480

with this one:

GRUB_GFXMODE=1280×1024

Step 3: Hit the ALT+F2 key combination, paste the following command and

check the “Run in terminal” option:

gksu gedit /etc/initramfs-tools/modules

When the text window appears, add the following line at the end of the file:

uvesafb mode_option=1280×1024-24 mtrr=3 scroll=ywrap

Step 4: Hit the ALT+F2 key combination, paste the following command and

check the “Run in terminal” option:

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash

Step 5: Hit the ALT+F2 key combination, paste the following command and

check the “Run in terminal” option:

sudo update-grub2

Step 6: Hit the ALT+F2 key combination, paste the following command and

check the “Run in terminal” option:

sudo update-initramfs -u

Step 7: Reboot your computer. When the system starts, you should see a better

looking Ubuntu logo!

The commands will only work for Grub2, not legacy.If you are using legacy

bootloader use the following instructions to install grub2 and follow the above

instructions

To install Grub2 before following the instructions on how to fix Plymoth screen.

sudo apt-get remove grub

sudo apt-get install grub-pc

sudo grub-install /dev/sda

sudo update-grub2


I performed Step 4 twice, once just as typed and a second time as two separate commands in the terminal. Also, I did not reboot between the typing of any of the commands. I think I might have simply rebooted after typing Step 4, but when the power came back up, a blank underscore appeared and blinked, got big for a moment, then went away never to be spotted again.

Right now, I've booted off of a live CD of Lucid for AMD 64 (I have a Dell laptop from which I'm sending this and which is the broken system I'm writing about).

Can anyone help me repair my old installation? I can see it via 'places' in the live CD environment. I have lots of configuration work and downloaded applications put into the prior installation and would rather repaire it than rebuild it.

Help!

Thank you for your attention,

Timothy Nugent

---

