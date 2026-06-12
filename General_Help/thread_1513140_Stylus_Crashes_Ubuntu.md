---
title: "Stylus Crashes Ubuntu"
date: 2010-06-19
forum: General Help
---

### Post by cntmn8td2006 on 2010-06-19
Issue: System crashes when using stylus
Cause: Including Option "PressCurve" "0,15,85,100" in xorg.conf


This is regarding the "10-wacom.conf" file located as follows.

```
cd /usr/lib/X11
cd xorg.conf.d
sudo gedit 10-wacom.conf
```

The issue appears to occur when I include the following line in the file named "10-wacom.conf."

```
Option "PressCurve" "0,15,85,100"
```

The issue is as follows.

After a system restart the first tap of the stylus on the screen causes the system to go black, and appears to crash the system.
The system then presents the log in screen. I log in, and go about using the stylus just fine. The system only crashes when I first use the stylus.

Changing the value "0,15,85,100" has not impact on the issue. 

Has anyone run into this issue? Does anyone have any suggestions as to how to trouble shoot this?

Thanks

---

### Post by Favux on 2010-06-19
Hi cntmn8td2006,

I gather you're in Lucid since you are using the 10-wacom.conf.  Can you tell me which Wacom tablet?  Also are you using the default Lucid 0.8.4-4 linuxwacom wacom.ko and 0.10.5 xf86-input-wacom?

Where are you adding PressCurve to the 10-wacom.conf?

We could try using xsetwacom.

---

### Post by cntmn8td2006 on 2010-06-19
Thank you for your help. I am using a Fujitsu T4210 table PC. The specs for this "Wacom tablet" are provided in the following link.

[http://www.fujitsu.com/downloads/COMP/fpcap/notebooks/previous/factsheet_lb_T4210.pdf]("http://www.fujitsu.com/downloads/COMP/fpcap/notebooks/previous/factsheet_lb_T4210.pdf")

The OS is a clean install with the latest updates. I don't know where I can find the versions for wacom.ko, and xf86-input-wacom. My guess is that they are the default files from the install.

I have included the exact text of the 10-wacom.conf file below.
Note that the text below is the default 10-wacom.conf except for the additional line "Option 'PressCurve' '0,15,85,100'."

```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
        Option "PressCurve" "0,15,85,100"
	
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```

My original issue was that the use of the stylus always behaved as if the stylus tip was pressed on the screen. Including "Option 'PressCurve' '0,15,85,100'" would modify the sensitivity of the stylus tip, and resolved my original issue. This unfortunately has led to my new problem.

Is there any other way of modyfying the sensitivity of the stylus tip?

Thanks

---

### Post by Favux on 2010-06-19
> I don't know where I can find the versions for wacom.ko, and xf86-input-wacom. My guess is that they are the default files from the install.
With a serial tablet pc you don't need to worry about wacom.ko, which is the usb kernel driver.  You just need xf86-input-wacom, which is in the xserver-xorg-input-wacom 0.10.5 package (it also has xsetwacom) in the Synaptic Package Manager.

OK, location of the PressCurve option line looks correct, so the first thing is to move it to the same location in this snippet.  Add it below the current serial snippet/section.  Boot with it unmodified then try the Press Curve line it it.
```
Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

```
Instead of adding the option to 10-wacom.conf you can also use xsetwacom.
```
xsetwacom set stylus PressCurve "0,15,85,100"
```
But you'll need to know what the kernel is calling your stylus by entering in a terminal:
```
xinput --list
```
Then either use the equivalent "Device name" (with the quotes) or the ID number instead of stylus.

The most recent xf86-input-wacom is 0.10.7 released in the last few days.  There have been xsetwacom fixes and I think fixes for serial tablets, so you may need to compile it or clone the git.  See Appendix 5 at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  But let's wait and see if we can get it working with the default first.

---

### Post by cntmn8td2006 on 2010-06-19
I have the modified the xorg.conf file as shown below.

```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
        Option "PressCurve" "0,15,85,100"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

```

Unfortunately, the addition of the snippet and "PressCurve" did not resolve the issue. It also appears the addition also had no impact on the original issue. 

Is there a way i can investigate the moment of crash? Say some sort of log.

---

### Post by Favux on 2010-06-19
Hi cntmn8td2006,

We can look at your Xorg.0.log in /var/log.  If that doesn't tell us enough we can add a debug option to the wacom.conf.

---

### Post by cntmn8td2006 on 2010-06-19
I tried looking over the log but I don't have enough experience to see what the problem is. I have uploaded the log if you wish to take a glance.  

I think I can cope with having my system crash one time if I truly wish to use the stylus.

---

### Post by Favux on 2010-06-20
Looks like it's blowing up on eraser:
```
II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/ttyS0"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(**) Option "PressCurve" "60,0,100,40"
(II) Serial Wacom Tablet: hotplugging dependent devices.
(**) Option "Device" "/dev/ttyS0"
(**) Serial Wacom Tablet eraser: always reports core events
(**) Option "PressCurve" "60,0,100,40"
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.
(--) Serial Wacom Tablet eraser: using pressure threshold of 7 for button 1
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=24576 maxY=18432 maxZ=127 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=2540 resol Y=2540
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=2540 resol Y=2540
```
You may be able to get more detail by adding:
```
Option "DebugLevel" "12"
Option "CommonDBG" "12"
```
That's the max. level (0-12) for both.  From:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)  I assume those are still both in xf86-input-wacom's xsetwacom.

If I recall correctly there are some other Fujitsu tablet pc user's seeing the same/similar thing (omskates?):
```
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
```
They also restarted X to fix it.

So this may be a bug in the code.  If you've messed with it a while longer getting no where I'd go ahead and clone the xf86-input-wacom git.  If that doesn't work file a bug report on the LWP's bug tracker.  I don't recall if that's been done yet.

---

### Post by cntmn8td2006 on 2010-06-20
I have included the following options

```
Option "DebugLevel" "12"
Option "CommonDBG" "12"
```

and I have attached the resulting log file. It does include additional material compared to before.

What do you mean by using a cloned xf86-input-wacom git? Is there a good reference I can use to read up on this?

---

### Post by Favux on 2010-06-20
Sure, see Appendix 5 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by Favux on 2010-06-20
Nice job!  Interesting.  The eraser blow up isn't seen this time:
```
II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/ttyS0"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(**) Option "PressCurve" "60,0,100,40"
(II) Serial Wacom Tablet: hotplugging dependent devices.
(**) Option "Device" "/dev/ttyS0"
(**) Serial Wacom Tablet eraser: always reports core events
(**) Option "PressCurve" "60,0,100,40"
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(II) Serial Wacom Tablet eraser: serial tablet id 0x93.
(--) Serial Wacom Tablet eraser: using pressure threshold of 0 for button 1
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=0 maxY=0 maxZ=0 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=0 bottom Y=0 resol X=2540 resol Y=2540
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=0 bottom Y=0 resol X=2540 resol Y=2540
```
But the backtrace may have caught the bug in the code:
```
Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x501410]
3: /usr/lib/xorg/modules/input/wacom_drv.so (0x19f000+0x891e) [0x1a791e]
4: /usr/lib/xorg/modules/input/wacom_drv.so (0x19f000+0x3c99) [0x1a2c99]
5: /usr/lib/xorg/modules/input/wacom_drv.so (0x19f000+0x3d7d) [0x1a2d7d]
6: /usr/bin/X (0x8048000+0x6d5bf) [0x80b55bf]
7: /usr/bin/X (0x8048000+0x122744) [0x816a744]
8: (vdso) (__kernel_sigreturn+0x0) [0x501400]
9: /usr/bin/X (0x8048000+0x2a1b0) [0x80721b0]
10: /usr/bin/X (0x8048000+0x1ed7a) [0x8066d7a]
11: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x1d5bd6]
12: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Floating point exception at address 0x1a5e94

Caught signal 8 (Floating point exception). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
```
That's the first time I've seen that Floating point exception.  Then:
```
(II) UnloadModule: "wacom"
(II) Serial Wacom Tablet: removing automatically added devices.
(II) UnloadModule: "wacom"
```
So if a newer xf96-input-wacom doesn't work you've now got something to report.

By the way a .txt file (Text Editor/gedit) is more useful.

---

### Post by chaosdx on 2010-06-20
Having the same model of laptop, I replicated 10-wacom.conf of **cntmn8td2006**, built 0.10.7 from source, and here is what I get after a reboot: 

```
(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS1)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.7
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/ttyS1"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet stylus: always reports core events
(**) Option "DebugLevel" "12"
(**) Option "CommonDBG" "12"
(**) Option "PressCurve" "0,15,85,100"
(**) Option "TopX" "0"
(**) Option "TopY" "0"
(**) Option "BottomX" "24576"
(**) Option "BottomY" "18432"
(**) Option "Button1" "1"
(**) Option "Button2" "2"
(**) Option "Button3" "3"
(II) Serial Wacom Tablet stylus: hotplugging dependent devices.
(**) Option "Device" "/dev/ttyS1"
(**) Serial Wacom Tablet eraser: always reports core events
(**) Option "DebugLevel" "12"
(**) Option "CommonDBG" "12"
(**) Option "PressCurve" "0,15,85,100"
(**) Option "TopX" "0"
(**) Option "TopY" "0"
(**) Option "BottomX" "24576"
(**) Option "BottomY" "18432"
(**) Option "Button1" "1"
(**) Option "Button2" "2"
(**) Option "Button3" "3"
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(II) Serial Wacom Tablet eraser: serial tablet id 0x93.
(--) Serial Wacom Tablet eraser: using pressure threshold of 27 for button 1
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=0 maxY=0 maxZ=0 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=2540 resol Y=2540
(II) Serial Wacom Tablet stylus: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS)
(--) Serial Wacom Tablet stylus: top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=2540 resol Y=2540
```

No errors, stylus works (for movement) as expected.

(On the other hand, even with this configuration, stylus buttons still don't work from onset. I have to relogin, get 
```
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.
(--) Serial Wacom Tablet eraser: using pressure threshold of 27 for button 1
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=24576 maxY=18432 maxZ=127 resX=2540 resY=2540  tilt=disabled
```
 in Xorg.log, and then every function works ok.)

---

### Post by Favux on 2010-06-20
OK, so maybe the pressurecurve commit mostly fixed it.

How are you setting up the stylus buttons?  Have you tried xsetwacom commands in a script?

It has stylus, two buttons (rocker switch), and an eraser?

What does your 'xinput --list' look like now?

---

### Post by chaosdx on 2010-06-20
> **Favux said:**
> OK, so maybe the pressurecurve commit mostly fixed it.

How are you setting up the stylus buttons?  Have you tried xsetwacom commands in a script?

It has stylus, two buttons (rocker switch), and an eraser?

What does your 'xinput --list' look like now?

Perhaps, the issue with buttons not working should be discussed in the original [http://ubuntuforums.org/showthread.php?t=1480639](http://ubuntuforums.org/showthread.php?t=1480639) thread.

Here I'll just note that, looking at the source of 0.10.7 version, it seems that "0x93" doesn't match actual T4210 capabilities, while "0x90" does. C is not normally my cup of tea, but the relevant piece of code isn't too complicated, so I hope to play around with it and report my findings in a couple of days.

---

### Post by Favux on 2010-06-20
Ahhh, right.  In fact in wacom.rules:
```
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0093", SYMLINK="input/tablet-tpc93-$env{WACOM_TYPE}"
```
is my model, a usb tablet pc with single finger touch.  And you are probably right, you want:
```
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0090", SYMLINK="input/tablet-tpc90"
```
Sounds like you know way more C than I do.  But with a serial tablet it shouldn't be in the wcmUSB.c table.  The wcmValidateDevice doesn't look like it's doing any assigning:
```
		case 0x90: /* TPC */
			priv->common->tablet_type |= WCM_TPC;
			priv->common->tablet_type |= WCM_LCD;
			break;
```
So my guess is somewhere in wcmISD4.c?:
```
	/* 0x9a and 0x9f are only detected by communicating
	 * with device.  This means tablet_id will be updated/refined
	 * at later stage and true knowledge of capacitive
	 * support will be delayed until that point.
	 */
	if (id >= 0x0 && id <= 0x7)
		tablet_id = 0x90;
	else if (id >= 0x8 && id <= 0xa)
		tablet_id = 0x93;
	else if (id >= 0xb && id <= 0xe)
		tablet_id = 0xe3;
	else if (id == 0x10)
		tablet_id = 0xe2;

	return tablet_id;
}
```

---

### Post by chaosdx on 2010-06-21
> **Favux said:**
> 
So my guess is somewhere in wcmISD4.c?


Yes, of course, as it is a ISDV4 device.

[COLOR="Silver"]No C programming since my uni days :p[/COLOR] At the very least, I hope to add more debugging output and find out why a cold start causes the tablet to report as "0x93" and have "maxXYZ"==0. And whether it is the cause of all the trouble or makes no difference.

---

### Post by Favux on 2010-06-21
Could the tablet be misidentifying itself?  You might want to look at udevadm info. and check on what Product ID it is returning:
```
udevadm info --export-db > $HOME/udevadm-info.txt
```

---

### Post by chaosdx on 2010-06-21
> **Favux said:**
> Could the tablet be misidentifying itself?  You might want to look at udevadm info. and check on what Product ID it is returning:
```
udevadm info --export-db > $HOME/udevadm-info.txt
```

That doesn't seem to be the case, or I'm just not searching well enough.

However, there is another curious thing going on after a relogin: 

```
P: /devices/virtual/vc/vcs8
N: vcs8
S: char/7:8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs8
E: MAJOR=7
E: MINOR=8
E: DEVNAME=/dev/vcs8
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:8 

P: /devices/virtual/vc/vcsa8
N: vcsa8
S: char/7:136
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa8
E: MAJOR=7
E: MINOR=136
E: DEVNAME=/dev/vcsa8
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:136
```

Those two virtual console devices don't appear in the attached udev info file. Those lines are there only after an X restart. Again, not sure what to make of it yet.

---

### Post by Favux on 2010-06-21
Hi,

Did you get the udevadm info. when the stylus wasn't working?  If so let's get one with it working.
```
P: /devices/pnp0/00:03
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:03
E: SUBSYSTEM=pnp
E: NAME=Serial Wacom Tablet
E: ID_INPUT=1
E: ID_INPUT_TABLET=1

P: /devices/pnp0/00:04
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:04
E: DRIVER=serial
E: SUBSYSTEM=pnp
E: NAME=Serial Wacom Tablet
E: ID_INPUT=1
E: ID_INPUT_TABLET=1

P: /devices/pnp0/00:04/tty/ttyS1
N: ttyS1
S: char/4:65
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:04/tty/ttyS1
E: MAJOR=4
E: MINOR=65
E: DEVNAME=/dev/ttyS1
E: SUBSYSTEM=tty
E: ID_INPUT=1
E: ID_INPUT_TABLET=1
E: DEVLINKS=/dev/char/4:65
```
You're right that isn't populated.  No Vendor ID (056a) or Product ID, etc.  Besides why does it think there is a tablet on ttyS1?  I'm pretty sure it should be on ttyS0.
```
P: /devices/platform/serial8250/tty/ttyS0
N: ttyS0
S: char/4:64
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS0
E: MAJOR=4
E: MINOR=64
E: DEVNAME=/dev/ttyS0
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:64
```

---

### Post by chaosdx on 2010-06-21
When stylus is detected "properly" the udevadm info is *exactly* the same, plus the two sections I posted earlier.

Which is not surprising, given that, even when maxXYZ are set to 0, the stylus is still kind of detected, and its movement is captured (see the other thread).

I'm not too concerned with ttyS0 vs S1, though. Shouldn't it work either way? For all I know it might be IrDA via serial interface trying to claim ttyS0.

---

### Post by Favux on 2010-06-21
Hmmm, OK.  No you're right.  With the two 10-wacom.conf snippets for serial being:
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

```
There's obviously enough in udevadm for the "Serial Wacom Tablet" MatchProduct to grab.

---

### Post by Favux on 2010-06-22
Hi,

Something interesting just happened.  Peter at the LWP just split ISD4 from usb in a new git branch serial-rework:  [http://sourceforge.net/mailarchive/forum.php?thread_name=20100622022502.GA17708%40barra.bne.redhat.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=20100622022502.GA17708%40barra.bne.redhat.com&forum_name=linuxwacom-devel) and [http://cgit.freedesktop.org/~whot/xf86-input-wacom/log/?h=serial-rework](http://cgit.freedesktop.org/~whot/xf86-input-wacom/log/?h=serial-rework)

If you test it and still have the same problem I bet you could get quick action.  He's looking for testers and feedback.  A thought anyway.

---

### Post by cntmn8td2006 on 2010-10-20
[B][U]SOLUTION
[/U][/B]
The latest xf86-input-wacom resolves the issue. You can update your xf86-input-wacom by beginning on Step 2 in the following link. Follow each direction, and read every little thing.

[http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

---

