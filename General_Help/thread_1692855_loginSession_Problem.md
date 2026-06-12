---
title: "login/Session Problem"
date: 2011-02-22
forum: General Help
---

### Post by sleepwalka26 on 2011-02-22
I am currently running xubuntu 10.04 had some random "glitches" where my screen would black out then exit the session to the login screen, as if I had commanded a reboot, up until recently its been a minor trouble. However now I can not log in at all, only from command line (using recovery feature at GRUB selection) I dont know what files may be corrupted, I'm decent at command line and can try to pull up any further information if need be for any help. I'd like to keep my current set up or at least not lose the files I have on my system.

---

### Post by sikander3786 on 2011-02-22
First of all, you can try reconfiguring your graphics from the command line.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Capital 'X' for X11.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

---

### Post by Old *ix Geek on 2011-02-22
If you installed on separate partitions, i.e., one for the file system and [at least] one for user data, you can reinstall the OS without losing any of your personal files. These would typically be / for the OS and /home (and possibly other partitions) for user files.

---

### Post by sleepwalka26 on 2011-02-22
Upon getting to command line via (Recovery Mode) I attempted @sikander3786's suggestion, how ever it was unsuccessful in that ```
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory

``` 
here is what I find inside of the X11 folder:
```
sleepwalka@laptop:~$ cd /etc/X11
sleepwalka@laptop:/etc/X11$ ls
[COLOR="RoyalBlue"]app-defaults[/COLOR]             rgb.txt             [COLOR="Lime"]Xreset[/COLOR]      [COLOR="RoyalBlue"]Xsession.d[/COLOR]
[COLOR="RoyalBlue"]cursors[/COLOR]                  [COLOR="Cyan"]X[/COLOR]                   [COLOR="RoyalBlue"]Xreset.d[/COLOR]    Xsession.options
default-display-manager  [COLOR="RoyalBlue"]xinit[/COLOR]               [COLOR="RoyalBlue"]Xresources[/COLOR]  XvMCConfig
[COLOR="RoyalBlue"]fonts[/COLOR]                    xorg.conf.failsafe  [COLOR="lime"]Xsession[/COLOR]    Xwrapper.config

```

@Old *ix Geek when I installed previous *ubuntu I would make separate partitions, however this install I followed the GUI install and do not remember if I used a separate partition for /home, /, and etc


**I would like to comment that using the (recovery Mode) I was able to log in using minimal graphics settings for one session**

---

### Post by JKyleOKC on 2011-02-22
For the past year, the /etc/X11/xorg.conf file has not been included in clean installs. However, you can copy the xorg.conf.failsafe file to xorg.conf in that directory, using "sudo cp xorg.conf.failsafe xorg.conf" to do so (after cd'ing into the directory of course), and then @sikander3786's suggestion should work for you.

These newer versions use an X driver that does not require xorg.conf to work, but will honor settings in that file if it exists. Many folk have found that the automatic setup in the newer versions fails to properly detect their video and restricts them to low resolution, or worse yet no GUI at all.

Hope this helps!

P.S. -- you can use the command "mount" in Terminal to determine whether you have a separate /home partition or not. If you have one, it will be listed; if it's not listed, then it's inside the / partition.

---

### Post by sleepwalka26 on 2011-02-23
Sorry for delay in reply, Upon further attempts to fix the "problem", I can copy the xorg.conf.failsafe file and create a new xorg.conf file, however ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` seems to do nothing, the files (xorg.conf.failsafe and xorg.conf) are identical, is ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` supposed to alter the xorg.conf file?

also is there a different workaround as far as the new way that the X driver works? any clues/tips/hints as to what I could do or code to offer here to help diagnose the the problem/solution? any ideas/help are appreciated.

---

### Post by JKyleOKC on 2011-02-23
It may change the xorg.conf file, but basically it uses the same not-always-accurate hardware detection routines that have already failed you. However this give a starting point.

You haven't said what kind of video card/chip you have; the command "lspci" should list all of your peripherals (other than disk drives) and one of them should include the word "video" or initials "VGA" which will be your video card/chip. Copy that line and paste it into a message so we can perhaps give you some additional details.

Meanwhile, edit that xorg.conf file's "Device" section to make it look like this if it does not already. The "vesa" driver is one that works with almost all video cards/chips; it doesn't provide all the eye candy of other drivers, but it works:```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection
```

Hang in there and we'll pborably get you up and running fairly quickly...

EDIT: To troubleshoot in more detail, look at the file "/var/log/Xorg.0.log" searching especially for lines that begin with (WW) or (EE) which are warnings and errors respectively. Several warnings are normal, especially one about the Cyrillic font not being found. Others, however, may be leads toward the problem, and all errors may well be.

Note the upper-case X in that log file name, and it's a zero, not an uppercase O, in the middle of the name.

---

### Post by sleepwalka26 on 2011-02-24
Alright, my graphics card is:
```
laptop:~$ lspci | grep VGA
01:05.0 [COLOR="Red"]VGA[/COLOR] compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

```
Here is _all_ that is in my xorg.conf, I did alter it as u suggested. 
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Also no need worry about "eye candy" I just want to be able to log into xubuntu, browse the Internet, work on assignments for school, Skype Video chat, etc.

---

### Post by sleepwalka26 on 2011-02-24
Also the I went to the /var/log/Xorg.0.log I didn't know if the whole file was necessary or if the sections that were (WW) or (EE) but nothing came up when I searched for (EE):

```
laptop:~$ grep WW  /var/log/Xorg.0.log
	([COLOR="Red"]WW[/COLOR]) warning, (EE) error, (NI) not implemented, (??) unknown.
([COLOR="red"]WW[/COLOR]) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
([COLOR="red"]WW[/COLOR]) Falling back to old probe method for vesa
([COLOR="red"]WW[/COLOR]) Falling back to old probe method for fbdev

```

btw "fbdev" was the original entry "Device" section in the /etc/X11/xorg.conf file I copied from the /etc/X11/xorg.conf.failsafe

---

### Post by JKyleOKC on 2011-02-24
The boot sequence uses "fbdev" during the first part of its action, then once the X server is loaded and active, switches to the other driver which in this case would be "vesa" for normal operation. This is why you will get short periods of a black screen, during the switchover.

However since the vesa driver is not making a difference, I don't think that the X server itself is your problem -- even though it's the most common reason for this sort of trouble. Looking closely at your original post, about the screen going black and returning to the login screen, suggests that you may have a damaged "gdm" service (the GNOME Display Manager, which Xubuntu also uses to handle login and starting the X server).

Try the command "startx" from a recovery mode login and see if that works. It won't give you the normal login dialog but may bring back your GUI -- and if it fails, it may give you some error messages that can help pinpoint the problem.

If startx works properly that will totally absolve the X server and xorg.conf file. Reboot, and try "sudo service gdm start" to manually launch the gdm service. If that works, you know we're on the right track and can concentrate on getting it to start automagically during normal boot. If not, any error messages will be helpful.

I have an appointment with my cardiologist this morning so will be out of touch for several hours but this should at least get you a bit of progress, and some of the others may have additional ideas for troubleshooting. Good luck!!!

---

### Post by sleepwalka26 on 2011-02-25
Sorry for delay, I had a full day of work yesterday and then a full day of classes today so I didn't have much time to try suggestions. I attempted as proposed and was met with some resistance when I tried to enter ```
startx
```
for kicks and giggles I tried "sudo service gdm start" and that led to```
gdm-binary [1020]: Warning : Unable to find users no seat-id found
[1020]Gdm Display : display lasted 0.289069 seconds <(this repeated a few more times)
GdmLocalDisplayFactory: Maximum number of X display failures reached: Check X server log for errors
```
I don't know exactly what I did, to create this error for the X server, but when I booted up I decided to be a brave little toaster and clicked some of the features in the recovery mode dialog and am able to log into my regular session, however looking at the /var/log/Xorg.0.log file I still have (EE) and (WW) popping up for 
```
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:05:0
(EE) VESA: Kernel modesetting driver in use, refusing to load
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

as well as the cryllic error. What is needed to help get VESA to load properly, again I'm not looking to run any sort of "Eye-Candy" like compiz fusion on this system I tried that with Ubuntu and it just lead to headaches so I switched to xUbuntu for simplicity of Xfce. I just want to have: Skype calls, Multi-workspaces, Internet video, Virtual Desktop (for windows so I can work on my M$ Excel/Access homework for class)etc. So _**ANY**_ suggestions on helping with the errors to help keep the system from running in to errors or crashing are greatly appreciated.

---

### Post by JKyleOKC on 2011-02-25
It may not seem like it, but you're making progress!

At the grub menu when you first start up, press the "e" key to enter edit mode. Then scroll down to the line that begins with "linux" and press the "end" key. At the end of the line, type " nomodeset" with the leading space but without the quotes, and then press CTRL-X to boot the system. This will turn off the modesetting driver in the kernel and do away with the first error message you see in the Xorg.0.log file; that may also eliminate the second one and even make everything work right again.

This will only last for a single session; if it does clear things up, you can then edit the /etc/grub/default file (using "gksudo gedit" to do so) to add the "nomodeset" option right after the "quiet splash" options where they appear, and save the edited file. Then run "sudo update-grub" to compile the changed defaults into the grub.cfg file and you may be almost done.

If this gets you back to a good usable configuration you can stop at this point, or you can see about enabling the ATI proprietary drivers to replace the vesa driver. They may give you a bit better performance, and you can always fall back to "vesa" if they introduce any problem.

---

### Post by sleepwalka26 on 2011-02-25
Alright, I rebooted and entered everything, I got logged in alright how ever my only complaint(not trying to look a gifted horse in the mouth here) is my screen size on my laptop is 1440x900 however my only options are 1024x600 or smaller... Is this fixable?
also in the /var/log/Xorg.0.log I seem to have more errors now ```
(II) VESA(0): Total Memory: 2048 64KB banks (131072kB)
(II) VESA(0): Configured Monitor: Using hsync value of 54.66 kHz
(II) VESA(0): Configured Monitor: Using vrefresh value of 59.94 Hz
[COLOR="red"](WW)VESA(0): Unable to estimate virtual size
[/COLOR](II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
(II) VESA(0): Not using built-in mode "400x300" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[COLOR="red"](WW) VESA(0): No valid modes left. Trying less strict filter...
[/COLOR](II) VESA(0): Configured Monitor: Using hsync value of 54.66 kHz
(II) VESA(0): Configured Monitor: Using vrefresh value of 59.94 Hz
[COLOR="red"](WW) VESA(0): Unable to estimate virtual size[/COLOR]
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
(II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
(II) VESA(0): Not using built-in mode "400x300" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[COLOR="red"](WW) VESA(0): No valid modes left. Trying aggressive sync range...
[/COLOR](II) VESA(0): Configured Monitor: Using hsync range of 31.50-54.66 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-59.94 Hz
[COLOR="red"](WW) VESA(0): Unable to estimate virtual size
[/COLOR](II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
(II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
(II) VESA(0): Not using built-in mode "400x300" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): Display dimensions: (370, 230) mm
(**) VESA(0): DPI set to (70, 84)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (123)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (122)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 131072 kB
(II) VESA(0): VESA VBE OEM: ATI RADEON XPRESS 200M Series
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: MS48
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(II) VESA(0): virtual address = 0xaf5ad000,
	physical address = 0xc8000000, size = 134217728
(II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
```

---

### Post by sleepwalka26 on 2011-02-25
Also, I'd like to add I retraced my steps to my previous post to being a "brave little toaster". I was able to because the session I was in "logged out" on its own after blacking out with some command line text then to the login screen. I restarted and was prompted with a dialog box notifying me about the Xserver error. I followed the following Reconfigure Graphics > Create New Configuration For This Hardware > A New Configuration Has Been Generated. Then I selected "restart X server" and was then brought to the login screen. I'm sorry if my posts are confusing, as said before any need for information from logs or commands or anything feel free to ask, I'm fairly decent with Terminal commands and etc.

---

### Post by JKyleOKC on 2011-02-25
Those WW warning messages in your log can be ignored for the time being since it's more or less working.

I had the same problem of a 1440x900 LCD monitor and only 1024x768 settings available from the driver. I finally got mine solved on this system by activating the Nvidia restricted driver and using their configuration package, which was able to get the data from the monitor and provide the right definition settings. You might explore the ATI driver for your system; the only box here that has an ATI card in it also has only a 1024x728 CRT monitor so I could not check on it. I do have a third system with an SIS card in it that uses this same LCD monitor; I installed Debian Sqeeze on it just a few days ago, and it has no xorg.conf file. The automatic setup detected this Acer X173w monitor and provided 1440x900 with no action on my part.

You might try renaming the xorg.conf file to xorg.conf.good and then rebooting to see if the same thing happens for you. If this brings back the original problem, then change the file name back and you should be in the same shape you are now.

Hopefully someone else will chime in here and tell you how to set up a modeline to add to your xorg.conf file. That will probably do exactly what you want, but if it's not set up properly can cause permanent damage to the monitor, and I don't remember all the steps!

---

### Post by sleepwalka26 on 2011-02-28
I have taken a little time off from repairing the problem to try and regroup my thoughts and what not. However, I'm currently at my college computer, researching the proprietary ATI drivers, and will attempt to get it up and working later on today after class. Although I haven't had any major problems with my setup as of recently since I opted to login using XFCE manager rather than another option( cannot clarify right now due to me not being on my laptop.)

---

