---
title: "graphic glitches on boot up after upgrade"
date: 2010-05-12
forum: General Help
---

### Post by HH60Gunner on 2010-05-12
After upgrading to ubuntu 10.04 whenever I boot up or shut down.  The screen goes black and there are weird multi-colored lines that move around the screen.  Eventually it boots up or shuts down as needed, but I guess I'm just being a little OCD and don't like this un-intended occurence.

---

### Post by blueridgedog on 2010-05-12
This is a known bug/issue with Plymouth.  

See the sticky for the release:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by HH60Gunner on 2010-05-12
Thanks,  

I'll try the fixes as soon as I get home :)

---

### Post by HH60Gunner on 2010-05-13
hmmm...

So I opened the file in gedit to modify with the line addition since I have an NVIDIA card however the file was completely blank.  Should I be worried?  Right now everything on my pc is working fine except for the weird graphics glitch on boot up

---

### Post by ryan858 on 2010-05-13
If you did it from command line, then my first guess would be that you mistyped it and  didn't actually open the file...

Try opening a Nautilus and click your way to /etc/default then double click 'grub'.

if it's still blank then that's really weird... and you should paste the following into it:

> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

And change it as needed, then save.

---

### Post by HH60Gunner on 2010-05-17
ok, the file didn't even exist.  So I created one and added that configuration to it but using my resolution.  It didn't do anything at all though.

---

