---
title: "Splash Screen"
date: 2010-05-07
forum: General Help
---

### Post by Drastic2010 on 2010-05-07
Hey guys,

All i want to do is install a new splash screen for when i boot up my box.  I've picked out the one and want, saved the file as a .tar.gz.  Just curious as to what i do next.

Thanks in advance for any help.  Sorry for the noob question, just new to Ubuntu.

---

### Post by Ginsu543 on 2010-05-08
Some questions to clarify what you want to do. When you say "splash screen" do you mean: (a) the background image that comes up when you enter grub; or (b) the background image that comes up when you are asked to log in; or (c) the background image that comes up when you are fully booted up and on the desktop?

Assuming you mean (a), i.e., the splash image for grub, then the next question is: which version of grub are you using? Grub-legacy (version 0.9x) or Grub2 (version 1.9x). If you did a fresh install of Ubuntu 10.04 or 9.10, you have Grub2. If an earlier version, you may have Grub-legacy. I'm going to assume that you have the latest Grub2 (version 1.98 ) that came with Lucid Lynx. If not, just let me know and I'll see if I can help you with that.

To change the splash image in Grub2 (1.98 ), you need to make a few changes in /etc/default/grub and in /etc/grub.d/05_debian_theme files. Bring up Terminal and sudo gedit /etc/default/grub. Then make the following changes:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
**GRUB_GFXMODE=1920x1200  <-- Add this line and set it to the native resolution of your monitor**

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```Now, sudo gedit /etc/grub.d/05_debian_theme and make these changes:

```

#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else

**** Comment out the original splash image** **
#  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"

[B]** Add the following **
WALLPAPER="/directory_path_to_image/name_of_image.jpg"[/B]

COLOR_NORMAL="black/black"
COLOR_HIGHLIGHT="magenta/black"

fi

```Notice that you can also change the color of the text that will appear on top of the splash image. In my case, I changed the COLOR_NORMAL setting to "white/black" because "black/black" doesn't show up very well on top of my splash image. Also, with Grub2, splash images no longer have to be in tar.gz format. They can be in .jpg or .png or even .tga.

Once you make the changes and save the files, run sudo update-grub to regenerate grub.cfg. When you reboot, you should be able to see your new splash image.

Having said all this, if you're running Grub-legacy then we'll have to do all this over another way. :p

---

