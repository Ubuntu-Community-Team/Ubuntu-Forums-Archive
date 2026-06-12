---
title: "Cant get gnome to start at all"
date: 2010-07-27
forum: General Help
---

### Post by DJYoshaBYD on 2010-07-27
Hola, all.. Im having an issue getting GDM to start.. i recently reformatted my server, and put 10.04 on there.. loving it so far.. well, the whole time i was testing it, i left a monitor hooked up the whole time..

So, this weekend, i rearranged the room its in, and hooked it back up, with no monitor.. I can still SSH, ftp, and use gnump3d.. i mean, basically anything that does not need X will run.. just cant get it to start.. 

this is the error i get when trying to start it via an ssh session

> joo@server:~$ sudo gdm start
[sudo] password for joo:
gdm-binary[4572]: WARNING: Unable to find users: no seat-id found
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.819148 seconds
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.268763 seconds
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.267445 seconds
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.266933 seconds
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.267333 seconds
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.267236 seconds
gdm-binary[4572]: WARNING: GdmLocalDisplayFactory: maximum number of X display f
ailures reached: check X server log for errors
joo@server:~$

Im not really sure what happened.. any ideas? im thinking it has something to do with not having a monitor hooked up..

---

### Post by DJYoshaBYD on 2010-07-27
bump monster

---

### Post by stlsaint on 2010-07-27
1. Plug in monitor
2. reboot system
3. run command:
```
sudo /etc/init.d/gdm restart
```

---

### Post by DJYoshaBYD on 2010-07-27
tis a headless server.. i shouldnt have to have it plugged in to do that.. lol.. it worked fine on hardy.. 

I mean, yes, that will probably fix it, but there should be another way so that it starts GDM without having a monitor hooked up.. 

Here is the log

> root@server:/var/log/gdm# more :0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux server 2.6.32-23-generic #37-Ubuntu SMP Fri Jun
11 07:54:58 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=8bb492
5c-f107-46c5-975f-20d458ea1980 ro quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubun](http://www.ubun)
tu.com/support)
Current version of pixman: 0.16.4
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 27 09:27:00 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevic
es.
(--) using VT number 8

(--) PCI: (0:0:3:3) 10de:07da:105b:0d1f nVidia Corporation MCP73 Co-processor re
v 162, Mem @ 0xeff00000/524288
(--) PCI:*(0:0:16:0) 10de:07e3:105b:0d1f nVidia Corporation C73 [GeForce 7050 /
nForce 610i] rev 162, Mem @ 0xed000000/16777216, 0xd0000000/268435456, 0xee00000
0/16777216, BIOS @ 0x????????/131072
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
(==) AIGLX enabled
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.13.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.1.0
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched fbdev as autoconfigured driver 3
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 0.0.15
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
        compiled for 1.7.3.901, module version = 2.1.15
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.3.0
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 0.4.1
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
        RIVA TNT    (NV04)
        RIVA TNT2   (NV05)
        GeForce 256 (NV10)
        GeForce 2   (NV11, NV15)
        GeForce 4MX (NV17, NV18)
        GeForce 3   (NV20)
        GeForce 4Ti (NV25, NV28)
        GeForce FX  (NV3x)
        GeForce 6   (NV4x)
        GeForce 7   (G7x)
        GeForce 8   (G8x)
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
        RIVA TNT    (NV04)
        RIVA TNT2   (NV05)
        GeForce 256 (NV10)
        GeForce 2   (NV11, NV15)
        GeForce 4MX (NV17, NV18)
        GeForce 3   (NV20)
        GeForce 4Ti (NV25, NV28)
        GeForce FX  (NV3x)
        GeForce 6   (NV4x)
        GeForce 7   (G7x)
        GeForce 8   (G8x)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) [drm] nouveau interface version: 0.0.15
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 0.0.2
(II) NOUVEAU(0): Loaded DRI module
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(--) NOUVEAU(0): Chipset: "NVIDIA NV63"
(II) NOUVEAU(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): Output VGA-1 disconnected
(WW) NOUVEAU(0): No outputs definitely connected, trying again...
(II) NOUVEAU(0): Output VGA-1 disconnected
(WW) NOUVEAU(0): Unable to find initial modes
(--) NOUVEAU(0): Virtual size is 0x0 (pitch 0)
(==) NOUVEAU(0): DPI set to (96, 96)
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.5.0
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
(II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xe42410]
3: /usr/bin/X (InitOutput+0xcac) [0x80ba36c]
4: /usr/bin/X (0x8048000+0x1ebbb) [0x8066bbb]
5: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x199bd6]
6: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Segmentation fault at address 0x18

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional informati
on.

 ddxSigGiveUp: Closing log

---

### Post by DJYoshaBYD on 2010-07-27
bumplestiltskin..

---

### Post by DJYoshaBYD on 2010-07-27
bump

---

### Post by DJYoshaBYD on 2010-07-27
bumping along.. singing a song.. siiiidddee byyyy siddddeeee :)

---

### Post by DJYoshaBYD on 2010-07-27
bumpyyyyyyy

---

### Post by DJYoshaBYD on 2010-07-27
sigh.. this is about the 4th time i have tried to get help in these forums for different issues, and no one ever seems to want to put forth an effort to try.. which is very sad.. 

so again.. BUMP.. i hope this isnt like the last problem that i bumped for a week straight, and never even got an answer.. i had to figure it out myself, which took forever..

anyone even want to put forth the effort to hook up some community support? i do my part......

---

### Post by aphatak on 2010-07-27
Stupid question:  if this is a headless server, with no one logged in and no monitor, what would Gnome do?

---

### Post by DJYoshaBYD on 2010-07-27
no sir.. the only stupid question is the one you dont ask :)

basically, i dont just use it for serving media and whatnot.. i log into it for browsing from work (they block youtube and some car forums that i frequent), plus i use it for making fliers and experimenting with virtual machines remotely.. its more like a server that runs a gui, but i still only remote access it.. never hook up anything but a network cable and the power.. it worked fine with hardy, with no extra setup.. but it doesnt do it here.. im sure there is a way to, but i just have no clue where to even start looking

its a very fun toy to have.. haha

---

### Post by DJYoshaBYD on 2010-07-28
bump

> Hola, all.. Im having an issue getting GDM to start.. i recently reformatted my server, and put 10.04 on there.. loving it so far.. well, the whole time i was testing it, i left a monitor hooked up the whole time..

So, this weekend, i rearranged the room its in, and hooked it back up, with no monitor.. I can still SSH, ftp, and use gnump3d.. i mean, basically anything that does not need X will run.. just cant get it to start.. 

this is the error i get when trying to start it via an ssh session

[QUOTE]joo@server:~$ sudo gdm start
[sudo] password for joo:
gdm-binary[4572]: WARNING: Unable to find users: no seat-id found
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.819148 seconds
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.268763 seconds
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.267445 seconds
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.266933 seconds
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.267333 seconds
gdm-binary[4572]: WARNING: GdmDisplay: display lasted 0.267236 seconds
gdm-binary[4572]: WARNING: GdmLocalDisplayFactory: maximum number of X display f
ailures reached: check X server log for errors
joo@server:~$

Im not really sure what happened.. any ideas? im thinking it has something to do with not having a monitor hooked up..[/QUOTE]

---

### Post by linux18 on 2010-07-28
well the long way to do it: 
====================================================================
STEP 1:
-choose recovery mode at grub

STEP 2:
-drop to a root prompt

STEP 3:
-type: 
```
 
telinit 3 
```
 and login

STEP 4:
-then type:
```

 xinit 
```

STEP 5:
-when xinit starts type:
```

metacity & 
```
- for ubuntu OR:
```

compiz & 
```
- if you have it OR flux/openbox & - if you have it OR:
```

fvwm4 &  
```
- for xubuntu

STEP 6:
-then type:
```

 gnome-panel & 
```
-for ubuntu OR:
```

 xfce4-panel & 
```
-for xubuntu

STEP 7:
-lastly type:
```
 
nm-applet & 
```
-for networking
======================================================================

---

### Post by DJYoshaBYD on 2010-07-28
oooooooooo k..

like i said.. NO monitor, NO keyboard will be hooked up to this machine.. it has to start on its own (and should, because every other version of ubuntu i have used previously did)..

i cant drop to grub to do this, because it has nothing set up.. it should turn on, and go to GDM, and autologin, just like a normal desktop..

Try not to think of this computer as a server, per se.. Think of it as a headless workstation, that just happens to run server apps.. :)

---

### Post by DJYoshaBYD on 2010-07-28
bumpy bump bumpens

---

### Post by DJYoshaBYD on 2010-07-28
anyone got the balls to try and troubleshoot this? hahahaha.. i see alot of people that lurk in here and only answer the easiest stuff (not naming names), but this one, and a few others, have been sitting here for a while with no help..

come on, fellas :)

grow a pair and lets see if we can resolve this, as im sure solving this issue will help others in the future..

that being said, buuuuuuumpyyyyyyyyyy

---

### Post by DJYoshaBYD on 2010-07-28
bump

---

### Post by DJYoshaBYD on 2010-07-28
OK.. so i know for a fact its because the issue is because there is no monitor hookedup, so it wont let X start..

i have also figured out that this is mainly caused by the fact that X now detects everything on its own now.. i figured this out by trying to find xorg.conf.. doesnt exist on 10.04.. hahaha..

so, what i need to know now, is how to make X think I have a monitor hooked up? like, tell it in xorg.conf that there is a monitor there, even though there is not..

---

### Post by DJYoshaBYD on 2010-07-28
bump..

any help would be appreciated (besides telling me to plug a monitor in)

---

### Post by DJYoshaBYD on 2010-07-28
buuuuuuuuuuuummmmmmmmmmmmmp

---

### Post by DJYoshaBYD on 2010-07-28
well, since NO ONE had the balls to step to the plate, and i have spent the last 2 days looking, i finally found a bug report about this

568079

so, when i get home, im going to try somethings, and post them, so that I AM ACTUALLY CONTRIBUTING THIS FORUM.. unlike anyone else that even wanted to try and help.. like always..

honestly, this forum is almost a waste of time, because i NEVER get any useful help in here.. not one bit.. This kind of community support is what will shy people away.. it almost did to me when i first started with linux..

thanks for no help.. ill post my results/resolution:(

---

### Post by DJYoshaBYD on 2010-07-29
wellllll.. i fixed it.. if anyone is curious, feel free to ask how, cause i know for a fact it will come up..
 
Im also going to post a "how-to" on this, as well, since i see alot of other posts on other (more active) linux forums with people asking the same question, and everyone is clueless.. 

so much for comm support

still love linux though :)

---

### Post by renemadeira on 2010-09-21
Hi, DJYoshaBYD!

I have the same problem in my computer. My intention is not to run it headless, but sometimes I or anyone who uses it forgets to power on the monitor BEFORE starting the pc. When this happens, the nvidia driver is not loaded, and it shows some options to reconfigure the X.
If I choose to go commandline mode and run "sudo nvidia-xconfig" and after "startx" everything goes ok.
The fact is that I'm not the only one who uses the computer, and the other users can't do these steps.
I'm running Lucid Lynx x64, and my graphics card is the same as yours.
$ lspci:
00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7100 / nForce 630i] (rev a2)

If you tell me the steps you did to make it get to work, I would be thankful.

---

