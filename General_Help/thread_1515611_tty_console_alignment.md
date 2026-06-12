---
title: "tty console alignment"
date: 2010-06-22
forum: General Help
---

### Post by bjacks on 2010-06-22
I'm sorry if this has been answered.  I have searched the forums and Google but don't quite find it.  I have Lucid installed on an AMD 64 machine with an Nvidia video card and the newest proprietary driver.  I have adjusted my monitor with the external buttons to align the desktop.  When I exit the desktop to a shell I get the login screen but it is misaligned to the left and many words are cut off.  I have adjusted the resolution and color to what I like and for the most part really like 10.04.  I use the console shells a great deal.  Thanks in advance.

:p

Brent

---

### Post by bjacks on 2010-06-22
I was able to fix this.  Here's a copy of my /etc/default/grub file:
[INDENT]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024x16
[COLOR=Red]GRUB_GFXPAYLOAD_LINUX=1024x768x16[/COLOR]  { =keep; did not work for me }
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

[/INDENT]Don't forget sudo update-grub

also:  sudo dpkg-reconfigure update-console allows changing the console font and font size.

Brent

---

