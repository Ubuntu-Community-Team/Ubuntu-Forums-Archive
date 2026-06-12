---
title: "karmic splash screen changes sizes/res with external monitor attached (on of off)"
date: 2009-11-24
forum: General Help
---

### Post by brookie on 2009-11-24
Hello,

I noticed that on one of my machines when I connect an LCD TV out on VGA and set it up the splash screen changes resolutions on boot up. 

Main laptop screen res: 1400x1050
TV res: 1360x768

This happens on reboot even if I have the monitor turned off in System>Preferences>Display

If I disconnetct the VGA cable the splash screeen shows up normal sized and centered on my laptop 1400x1050 screen. The usplash resizing only occurs when the external monitor is physically connected (on or off in Display properties). 

I can't take a screen shot of this but it looks like during boot everything is normal, black screen with white ubuntu logo, then cool "Ubuntu" usplash screen with bar running on bottom, ...

...then the screen flashes and the splash screen is resized to take a smaller resolution and is oriented in the upper left two thirds of the screen with a black border on bottom and to the right of the smaller usplash. 

Dual screens work, just wanted to get rid of this anoyance. Maybe it's a bug. BTW, I installed start up manager and then uninstalled it as it hosed my grub but I have it back to normal now. I can't remember if it was doing this weird stuff before the SUM attempt. 


grub conf: 
```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
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
```

SUM changed this to 640x480 an I changed it back
usplash.conf: 
```
cat /etc/usplash.conf
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1400
yres=1050
```


I have another laptop 1200x800 with an external display 1024x768, and the usplash screen does not resize itself on that machine. 

Any ideas? 

I gotta run and will check this later this evening. 

Thanks,
brookie

---

### Post by brookie on 2009-11-25
bump
does anybody know if this is a known bug or not? i've searched all over. or is it a WAD?

---

### Post by SabreWolfy on 2009-12-05
Similar issue with Karmic with NVidia dual view. Worked nicely in Jaunty; splash screen and gdm  login appeared on only one monitor. Now in Karmic (upgraded from Jaunty), the throbber is spread badly over both monitors; login appears on one and then throbber returns over both until desktop appears.

PS: I don't have grub.conf ... My usplash is set to the resolution of the smaller monitor, although the throbber appears on the smaller monitor and overlaps onto the other one.

Look [here]("https://bugs.launchpad.net/ubuntu/karmic/+source/xsplash/+bug/420225") and [here]("http://http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg30580.html").

---

