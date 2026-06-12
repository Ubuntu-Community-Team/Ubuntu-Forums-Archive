---
title: "my xorg .conf and gconf is broken, help needed please"
date: 2011-02-19
forum: General Help
---

### Post by maddbaron on 2011-02-19
Hello,


reinstalled all my drivers in safe mode, rebooted and the result is the bottom image. 

Can anyone please tell me how to fix this kind of distortion?

Thanks in advance

---

### Post by maddbaron on 2011-02-19
bump...i know this is a minor issue that can be solved with some commands or re-installs i just don't know what to do....

help please

---

### Post by drdos2006 on 2011-02-19
Looks like the driver is not working.

Reboot with a LiveCd.

Right click to mount the file system drive in temporary mode

Edit /etc/xorg.conf with vi, type:
sudo vi /etc/xorg.conf
( Press ESC :w! to write, ESC :q! to quit from vi )
Remove "nvidia", or whatever the offending driver is, save and close, reboot.

Or you can boot into safe mode if you are familiar with terminal commands.
Press Left Shift Key after BIOS check and choose Recoverery mode from the menu, select drop down to boot into terminal mode from next drop down list.

good luck.

regards

---

### Post by maddbaron on 2011-02-19
> **drdos2006 said:**
> Looks like the driver is not working.

Reboot with a LiveCd.

Right click to mount the file system drive in temporary mode

Edit /etc/xorg.conf with vi, type:
sudo vi /etc/xorg.conf
( Press ESC :w! to write, ESC :q! to quit from vi )
Remove "nvidia", or whatever the offending driver is, save and close, reboot.

Or you can boot into safe mode if you are familiar with terminal commands.
Press Left Shift Key after BIOS check and choose Recoverery mode from the menu, select drop down to boot into terminal mode from next drop down list.

good luck.

regards

it's an ati fire gl driver. I've tried to install and reinstall it at least 3 times...is there a way for me to test if i have the most current version?  and do I type ati fire gl as the driver or just fire gl?

---

### Post by Krytarik on 2011-02-19
The proprietary ATI/AMD video driver is called "fglrx". But since it fails to load properly at the start of X, you should do it the other way around, the default open source driver is "ati".

So, boot into recovery mode, then choose root prompt, and edit your xorg.conf with the command:
```
nano /etc/X11/xorg.conf
```How did you install the driver?

I recommend doing a package based install of the driver instead of manually, to avoid having to re-install it everytime the kernel gets updated. The easiest/safest way is via "System -> Administration -> Hardware Drivers/Additional Drivers".

You may want to update the driver after that to the most recent packaged version:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

---

### Post by PaulReaver on 2011-02-19
THE EASY WAY :)


boot into your machine and press ctrl-alt-F1 and log in. if you must you can use safe mode.



sudo service gdm stop

sudo aticonfig --initial

sudo shutdown -r now


should fix your problem... set you up with a standard xorg.conf



if it doesn't come back we'll try something else...

---

### Post by maddbaron on 2011-02-28
my xorg is completely blank, I tried the above help and nothing worked, i went into safe graphics mode then gedit via terminal to open my xorg and its completely empty.  I tried running via livecd and that doesn't work (cd won't boot, drive works cd simply won't boot)...so i can't even if i have do a complete re-install... 

edit:

here is an output

```
ls -la /etc/X11
total 124
drwxr-xr-x  10 root root  4096 2011-02-20 10:54 .
drwxr-xr-x 178 root root 12288 2011-02-28 08:37 ..
drwxr-xr-x   2 root root  4096 2011-02-15 13:58 app-defaults
drwxr-xr-x   2 root root  4096 2011-02-15 14:00 cursors
-rw-r--r--   1 root root    14 2010-04-29 10:29 default-display-manager
drwxr-xr-x   6 root root  4096 2010-04-29 10:24 fonts
-rw-r--r--   1 root root 17394 2009-12-03 05:56 rgb.txt
lrwxrwxrwx   1 root root    13 2010-06-09 07:33 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2011-02-15 13:58 xinit
drwxr-xr-x   2 root root  4096 2010-04-15 08:12 xkb
-rw-r--r--   1 root root   684 2011-02-20 10:54 xorg.conf
-rw-r--r--   1 root root   264 2011-02-15 15:50 xorg.conf-backup-110215154939
-rw-r--r--   1 root root   264 2011-02-15 19:37 xorg.conf-backup-110215193653
-rw-r--r--   1 root root   264 2011-02-15 14:23 xorg.conf.dist-upgrade-201102151423
-rw-r--r--   1 root root   269 2011-02-28 08:36 xorg.conf.failsafe
-rw-r--r--   1 root root   684 2011-02-19 09:20 xorg.conf.fglrx-0
-rw-r--r--   1 root root   684 2011-02-20 10:40 xorg.conf.fglrx-1
-rw-r--r--   1 root root   264 2011-02-16 11:39 xorg.conf.old
-rw-r--r--   1 root root    87 2011-02-17 09:57 xorg.conf.original-0
-rw-r--r--   1 root root     0 2011-02-17 23:37 xorg.conf.original-1
-rwxr-xr-x   1 root root   709 2010-04-01 07:19 Xreset
drwxr-xr-x   2 root root  4096 2011-02-15 12:43 Xreset.d
drwxr-xr-x   2 root root  4096 2011-02-15 12:43 Xresources
-rwxr-xr-x   1 root root  3730 2010-04-01 07:07 Xsession
drwxr-xr-x   2 root root  4096 2011-02-19 09:19 Xsession.d
-rw-r--r--   1 root root   265 2008-07-01 13:41 Xsession.options
-rw-------   1 root root   601 2010-04-29 10:20 Xwrapper.config

```

I tried something else to view my xorg and its not empty but where it says display I see a 0 0 next to view point, should that be something else?..

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

also sorry for the late reply I had a family issue to deal with.

---

### Post by Krytarik on 2011-02-28
Your xorg.conf is fine, the default after creation with aticonfig or by the install process.

What is the current state of the driver installation, how did you install it?

---

### Post by maddbaron on 2011-02-28
> **Krytarik said:**
> Your xorg.conf is fine, the default after creation with aticonfig or by the install process.

What is the current state of the driver installation, how did you install it?

i used the wiki linked to ubuntu.com for ati drivers that i found linked to 10.10 after I upgraded and saw the previous issue I had, compiled it then installed it using terminal.  then i activated it. rebooted and still can't get a normal screen in regular boot-up. 
driver currently says active.

 originally my compiz wasn't working and the screen was flickering so I removed the ati drivers and compliz then reinstalled them, flickering stopped but I got this so I went to safe mode and activated the driver and the problem continues

my system is ati and amd so i removed the nvidia drivers, could that be causing this issue? is there something i can run in terminal to fix this?

---

### Post by Krytarik on 2011-02-28
It seems like you installed the driver manually from the website, is that right?

I do really recommend installing the driver the way I described earlier.
If you indeed installed it manually, remove it before before.

Apparently you didn't say so far, what card you have!? Is it really still supported by the proprietary driver?

And no, the removal of the nvidia packages won't interfere in any way.

---

### Post by maddbaron on 2011-02-28
> **Krytarik said:**
> It seems like you installed the driver manually from the website, is that right?

I do really recommend installing the driver the way I described earlier.
If you indeed installed it manually, remove it before before.

Apparently you didn't say so far, what card you have!? Is it really still supported by the proprietary driver?

And no, the removal of the nvidia packages won't interfere in any way.

my video card is a  Mobility Radeon HD 4200.. 

ok so remove the current install of the driver i have, reboot, install driver, reboot, activate driver, reboot? 
will do in the am...hopefully it works...

thank you for your help and patience.

this is the last upgrade I do for a while...setting up 10.04 wasn't this hard lol...next upgrade is going to be a clean install...lol

---

### Post by Krytarik on 2011-02-28
> **maddbaron said:**
> 
ok so remove the current install of the driver i have, reboot, install driver, reboot, activate driver, reboot? 

I would do it this way, should be sufficient:
- remove the current install of the driver
- install/activate new driver
- relogin

---

### Post by maddbaron on 2011-03-02
> **Krytarik said:**
> I would do it this way, should be sufficient:
- remove the current install of the driver
- install/activate new driver
- relogin

Finally Fixed! 
Thank you!

---

### Post by Krytarik on 2011-03-02
> **maddbaron said:**
> Finally Fixed! 
Thank you!
Cool, glad that it worked!

---

### Post by maddbaron on 2011-03-02
> **Krytarik said:**
> Cool, glad that it worked!

yeah i am glad i got my system back now to update my ppa's get my compiz back and get my desktop back to normal

---

