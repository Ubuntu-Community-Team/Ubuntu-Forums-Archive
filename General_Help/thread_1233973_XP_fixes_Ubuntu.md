---
title: "XP fixes Ubuntu"
date: 2009-08-07
forum: General Help
---

### Post by OBiiT on 2009-08-07
Hi,

I need some help if someone knows anything about this. I used to have XP but now have installed ubuntu also, so I can pick which one to use at start up. My problem is that every time Ive been using ubuntu and then reboot and start XP my graphical card are lost in XP. This happens every time. But when I start XP one more time then it is normal again.

This is not the only problem. When I run ubuntu and restart the comp and go in to ubuntu again, then I get some error messages which Ill write later.

So basicly, everytime I use Ubuntu my graphics disappears. So if I am now using ubuntu and start with ubuntu again next time ill get the errormessages below, and if i boot xp next time I will need to reinstall the graphics there. We can in a way say that what ubuntu destroys XP fixes.

And here is what it says when Ubuntu dont want to start:

Blue screen saying: Failed to start xserver.
Fail safe mode was already attempted within 30seconds.
Falling back to gdm to report

I press enter and the screen is back with white text saying:
Starting up..
Loading, pls wait...
19+0 records in
19+0 records out
kinit name_to_dev_t(/dev/disk/...)
kinit: trying to resume from /dev/disk/by-uuid/<some hex numbers>
kinit: No resume image, doing normal boot

And then it asks me to log on. but when I do... yeah I have no clue what to do.. no gui.

Someone who dare to guess what is happening and how to fix it? Thankfull for any guesses

---

### Post by NightwishFan on 2009-08-07
Do you have Ubuntu recovery mode available? It has an option at the boot (grub) screen. You can boot into there to reset the graphical configuration and xserver. That might help you.

From what I understand Ubuntu has no graphical display? Is Windows fine or broken as well?

---

### Post by martinbaselier on 2009-08-07
It looks like the error is caused by the driver of your graphical card.

When you boot into the terminal, make a copy of Xorg.0.log

I presume you are logged in under your own user name and in your home directory:

**sudo cp /var/log/Xorg.0.log .**
**sudo chown `whoami`:`whoami` Xorg.0.log**

Note the ` for whoami is a reversed ' (On us keyboards it's on the left side of the 1.) 

You can also create a script in your home directory and paste the commands into it. 

From a terminal in ubuntu (with gui) run:
gedit copylog.sh
paste the lines into it, save and exit
then reboot and run 
**sh copylog.sh**

When you've made the copy of your log, post it here. 

Also please post the output of **sudo lshw -c video**

You can copy and paste from a terminal. (use the code tags on the forum, and paste the output between those tags)

---

### Post by Sidewinder1 on 2009-08-07
This maybe "off the wall" but when I first installed Ubuntu, if I "warm-rebooted" (Restart), I had similar problems; I tried a cold- reboot, (shot-down computer, wait about 5 seconds and press start switch) and have been doing that ever since; no problems. Although I'm a little embarrassed to admit that I occasionally boot into windoze. ;-)

HTH, Side

---

### Post by Iowan on 2009-08-07
> **Sidewinder1 said:**
> if I "warm-rebooted" (Restart), I had similar problems; I tried a cold- reboot, (shot-down computer, wait about 5 seconds and press start switch) and have been doing that ever since; no problems. +1 
I've read elsewhere that machines can sometimess reboot in less time than it takes for some electronics to reset (capacitors discharge, or whatever) and drivers don't get completely reset.  The power-off reboot was suggested as a workaround.

---

### Post by OBiiT on 2009-08-08
I did try to shut down the comp and wait for a while before i started it again. But same thing happened. And also if I went in to recovery mode where I tried to fix xserver. I didnt see anything about how to reset the graphical settings. But same thing again after i did "fix xserver".

To clarify, when I start ubuntu it seems to do something to my graphical drivers. So when i have used ubuntu one time and restarts it these two scenarios can happen:

1. I boot Ubuntu and gets the error messages I posted, and no GUI. If I reboot with ubuntu another time the same thing happens over and over, no end.

2. I boot XP and it is without my usual graphical settings. It descovers that i in fact have a graphical card which it want to install some standard drivers for (these drivers doesnt work though). If I reboot with XP again my usual graphical card is fully functional, no problems at all. And if I reboot to ubuntu that is also working without any problems.


Here are the outputs that you were asking for:

From **sudo lshw -c video**
```
  *-display               
       description: VGA compatible controller
       product: Mobility Radeon HD 3400 Series
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

```From [B]copylog.sh
[/B]```


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux mattias-laptop 2.6.27-14-generic #1 SMP Fri Jul 24 22:19:33 UTC 2009 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug  8 14:52:51 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 4.1
    X.Org XInput driver : 2.1
    X.Org Server Extension : 1.1
    X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(!!) More than one possible primary device found
(--) PCI: (0@0:2:0) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xfc000000/0, 0xd0000000/0, I/O @ 0x00001800/0
(--) PCI: (0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3400 Series rev 0, Mem @ 0xc0000000/0, 0xbfff0000/0, I/O @ 0x00002000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 7.4.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.5.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.4.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
Primary device is not PCI
(==) Matched vesa for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.5.0, module version = 1.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: 
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

```

---

### Post by martinbaselier on 2009-08-08
The first output shows you have one video card, it's an ati hd 3400 and you are using the ati driver. 
The second output shows you have 2 video cards, one on the MB and one plugged in. It doesn't load the ati driver, but the vesa one. Since the kernel module of the ati driver normally is already loaded this won't combine well. This also suggest the ati card is turned off in some fashion.

Which version of the proprietary ATI driver are you using? 

Do you still have the problem when acpi is turned off.
Press **esc** while starting to enter grub, choose **e** to edit, then choose the second line and **e** again to edit, add **noacpi** on the end of the line, **enter**, **b** to boot.

---

### Post by bollix47 on 2009-08-08
Have you checked the Bios to see if there is a setting to disable onboard graphics?

---

### Post by OBiiT on 2009-08-08
I got the same result when i turned off acpi.

And im sorry, but I dont know how to see which driver I am using. I have not installed any drivers on my own, just using the ones that ubuntu installed for me during the installation. Any easy way to see this?

To disable the onboard driver? I found something saying "Default Primary Video Device: Internal/PCI Express" it was set to Internal but I tried PCI Express instead. But then again, same problem.

---

### Post by bollix47 on 2009-08-08
> **OBiiT said:**
> 
To disable the onboard driver? I found something saying "Default Primary Video Device: Internal/PCI Express" it was set to Internal but I tried PCI Express instead. But then again, same problem.

Okay, if your monitor is connected to the ATI card then you want that setting to be PCI Express.  You might have to reboot a couple times into both operating systems so that the proper settings are used.

XP should just pick up the new setting and work with it.

Ubuntu may require a reconfigure using:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by martinbaselier on 2009-08-08
You could try turning off the proprietary drivers. In your settings, go to restricted drivers and turn off the driver for your video card. This way the open source driver will be used and not the one created by ATI.

If that helps, check this guide to see how to install a new driver from ATI.
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
Maybe that will bring something.

---

### Post by OBiiT on 2009-08-08
Wow, I found a guide to that fixed the whole thing. [http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_T400]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_%28Intrepid_Ibex%29_on_a_ThinkPad_T400") Under the "Before installation" it said:


[LIST]
[*] Change to Internal or ATI Graphics with Config --> Display --> Graphics Device --> [Integrated graphics] or [Discrete Graphics]
[*] Disable OS Detection for Switchable Graphics. Otherwise it will mysteriously switch back to Switchable Graphics.
[/LIST]
that made it, it all works now. That guide is only for T400 but theres more guides for other models too there. Thanks for all help though.

---

