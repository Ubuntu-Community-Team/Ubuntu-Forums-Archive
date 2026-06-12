---
title: "Ubuntu 10.04.1: getty processes not running tty1-6 / ctrl+alt+f1-f6 terminals"
date: 2010-08-12
forum: General Help
---

### Post by jkrez on 2010-08-12
When I boot my computer the terminals ctrl+alt+f1-f6 only have a blank cursor. If I type into them the characters are simply left there and nothing happens.  

I've read about frame buffer problems with these terminals:
[http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454)
[https://wiki.edubuntu.org/FrameBuffer](https://wiki.edubuntu.org/FrameBuffer)

and about framebuffers with lucid:
[http://ubuntuforums.org/showthread.php?t=1292409](http://ubuntuforums.org/showthread.php?t=1292409)

and
[http://swiss.ubuntuforums.org/showthread.php?t=1181594](http://swiss.ubuntuforums.org/showthread.php?t=1181594)

and from this

[http://ubuntuforums.org/showthread.php?p=7973082#post7973082](http://ubuntuforums.org/showthread.php?p=7973082#post7973082)

I tried reinstalling coreutils

and nothings worked :/

Information:

```

$ ps -e | grep getty

```
returns nothing, and
```
$ ps -e | grep tty
  952 tty7     00:03:09 Xorg

```
gives only the Xorg tty7 process running
My video card:
```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

```
$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

I've read 
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash 3"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x800

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```


```
$ cat /etc/usplash.conf 
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1280
yres=800
```

(my laptop/main display is LVDS1, so I'm using my native resolution)

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+0+224 (normal left inverted right x axis y axis) 290mm x 180mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
```

I tried changing /etc/default/rcS 
DELAYLOGIN=no
to
DELAYLOGIN=yes
without success

```
$ cat /etc/default/rcS 
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no
```

I could do:
```
sudo start tty1
```
or make a script to run all of those on startup. But I'm trying to figure out what's causing this. Anyone know where those process are called / run from? If you need anymore information let me know.

---

### Post by eotakos on 2010-08-30
Hello,

I have the same issue more or less... in my case if I switch there where tty1 should be, I have the blinking cursor, and if I type something nothing happens at all (not even my input displayed). I can too start the tty1 with "sudo start tty1". On the other hand, my laptop runs on lucid too, and everything works just fine. 

A difference I see compared to my previous installation (8.04) is that when I pressed ctrl+alt+f8, I could see the commands executed at the end of the bootup process, whereas now it is just the blinking cursor (even for the laptop installation that works)

If I execute "status tty1", I get
[HTML]tty1 stop/waiting
[/HTML]

Does this mean that the process started as it should and for some reason it stopped (instead of the scenario that the process didn't start at all)? If that is the case, then maybe changing the "stop on" condition in /etc/init/tty1.conf (to -for example- "shutdown") could probably make a difference...


If you had any progress please do share...

---------------------------------------------------
EDIT:
after the last update, the problem seems to be solved -for me at least-. The same update also made my rc.local execute, which means that something was happening at the end of the init process... (I guess)

---

