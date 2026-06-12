---
title: "Can someone help me get started to make my Wacom tablet work please?"
date: 2010-05-26
forum: General Help
---

### Post by s3a on 2010-05-26
I have the Wacom Bamboo Pen CTL460M and would appreciate it very much if someone could at least get me started in the right direction. I tried Ubuntu 10.04 and it doesn't pick it up! Will Ubuntu 10.10 pick it up out of the box? What can I do to make it work before then? The instructions on the Wacom website seem difficult not because of what has to be done but in my opinion, the explanations are not great (not that they're that bad). I'd particularly like to get this to work on my Debian Lenny laptop with the 2.6.30 kernel. I had a functional pen but broke it accidentally and now, I'm in this situation. I broke it during my school semester so I had to use paper lol but a digital pen saves trees and also is good for organizing notes as well as preserving them, so it'd be great if someone could help me get this one working! It is also useful for me and my friends to help each other with our homework when we're not near each other.

Any help would be GREATLY appreciated!
Thanks in advance!

---

### Post by dino99 on 2010-05-26
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1038949&page=99](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1038949&page=99)

add this ppa to synaptic repo, then update upgrade

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

xserver-xorg-input-wacom need to be installed

---

### Post by Favux on 2010-05-26
Hi s3a,

To get it working in Lucid you need to compile a newer wacom.ko than the default 0.8.4-4 one, say 0.8.6-2.  See the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Read Lucid near the top and then Section 1.  With 0.8.6-2 you don't need to do the extra directory change described.

In Debian Lenny as long as the Xserver is 1.6.4 or lower then you would compile and install linuxwacom 0.8.6-2.  In other words in addition to the wacom.ko you would install the linuxwacom X driver (wacom_drv.so).

---

### Post by s3a on 2010-08-16
Sorry for the late response, I kind of have a way of doing that. School is about to start and I've been doing other things so I couldn't worry about my tablet but now I can. I would like to first do this on my Debian Squeeze computer.

_So, here is the stuff you mentionned:_

```
deniz@debian:~$ locate wacom.ko
/lib/modules/2.6.26-2-amd64/kernel/drivers/input/tablet/wacom.ko
/lib/modules/2.6.32-5-amd64/kernel/drivers/hid/hid-wacom.ko
/lib/modules/2.6.32-5-amd64/kernel/drivers/input/tablet/wacom.ko
deniz@debian:~$ locate wacom_drv.so
/usr/lib/xorg/modules/input/wacom_drv.so
deniz@debian:~$
```

_Here is the X version and where I am stuck:_
```
deniz@debian:~$ X -version

X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32-5-amd64 x86_64 Debian
Current Operating System: Linux debian 2.6.32-5-amd64 #1 SMP Sat Jul 24 01:47:24 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-5-amd64 root=/dev/mapper/debian-root ro quiet
Build Date: 15 July 2010  03:08:26PM
xorg-server 2:1.7.7-3 (Cyril Brulebois <kibi@debian.org>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[B]deniz@debian:~$ more /proc/bus/usb/devices
/proc/bus/usb/devices: No such file or directory
deniz@debian:~$ more /proc/bus/usb/devices
/proc/bus/usb/devices: No such file or directory[/B]
deniz@debian:~$
```

_I am following:_
[http://linuxwacom.sourceforge.net/index.php/howto/all#kernel](http://linuxwacom.sourceforge.net/index.php/howto/all#kernel)
3.1 - Testing Tablet Detection

---

### Post by Favux on 2010-08-16
Hi s3a,

It looks like Debian Squeeze is basically equivalent to Lucid.  See the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by s3a on 2010-08-17
I was on the *sudo apt-get install linux-headers-generic* step of your guide ([http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)) but the Debian repositories don't have that package. It must be named differently, do you know what the package name is?

---

### Post by Favux on 2010-08-17
I believe it's:
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by s3a on 2010-08-17
It is, thanks. :) (I actually already had it installed) I will continue and report later.

---

### Post by s3a on 2010-08-17
I have another problem.

X -version says: > X.Org X Server 1.7.7

and ./configure --enable-wacom --prefix=/usr says:
> NOTE: this package only supports Xorg server older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.

I am assuming this means I need to compile a newer version of some wacom program (since xf86-input-wacom is not part of the repositories), I am confused as to which package this is. Is it in the Debian repositories because all I see is: [http://packages.debian.org/search?suite=all&section=all&arch=any&searchon=names&keywords=wacom](http://packages.debian.org/search?suite=all&section=all&arch=any&searchon=names&keywords=wacom) Or is it not in any repositories and I have to get it upstream? Also, I checked and linuxwacom-0.8.8-8 is the latest wacom has to offer, so why does it not support the latest X?

---

### Post by Favux on 2010-08-17
That's just poor wording.  What they are trying to say is linuxwacom won't build the Xdriver for Xserver 1.7 or later, instead you need xf86-input-wacom for the Xdriver.  However the wacom.ko from linuxwacom will build fine.

It's funny you mention it because they're trying to reword because two many folks are asking questions about it like you are.  So now it says:
+       echo "NOTE: the X driver in this package only supports Xorg servers older than 1.7."
       echo "          You are running a newer version. "
       echo "Please build the X driver from xf86-input-wacom."
+       echo "The kernel driver provided in this package is independent of "
+       echo "the X server version"

So now it's crystal clear, right?

---

### Post by s3a on 2010-08-17
> Note: The X driver in this package only supports Xorg servers older than 1.7. You are running a newer version. Please build the X driver from xf86-input-wacom. The kernel driver provided in this package is independent of the X server version's driver and both are needed for the tablet(s) to work.

is more clear, assuming I am right (sorry, if I am not).

Also, a little more of a really brief introduction about xf86-input-wacom would help make the explanation even better; again assuming that what I'm saying is correct. Is it?

---

### Post by Favux on 2010-08-17
Almost right.  Any recent wacom.ko would probably work.  Only usb tablet's need wacom.ko's.  The default wacom.ko in Lucid is from 0.8.4-4, which works for most tablets.  However the Bamboo P&T's are so new that it doesn't work for them and you need a newer one.
> Also, a little more of a really brief introduction about xf86-input-wacom would help make the explanation even better;
These kind of comments in the code are always terse.

---

### Post by s3a on 2010-08-17
Sorry I did not quite catch what was wrong in what I had said earlier. All I understood is that wacom.ko is only for USB users and of course my tablet is too modern which I already knew.

Is wacom.ko from the package I am trying to build or is it X's driver? And where do I get xf86-input-wacom? It seems that wacom's website only has linuxwacom. It also seems Ubuntu and Debian don't have it in the repositories:

[https://launchpad.net/ubuntu/+source/xf86-input-wacom](https://launchpad.net/ubuntu/+source/xf86-input-wacom)

[http://packages.debian.org/search?suite=all&section=all&arch=any&searchon=names&keywords=xf86-input-wacom](http://packages.debian.org/search?suite=all&section=all&arch=any&searchon=names&keywords=xf86-input-wacom)

[http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=xf86-input-wacom](http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=xf86-input-wacom)

Also, what is the difference between xf86-input-wacom, linuxwacom wacom.ko wacom_drv.so, and xserver-xorg-input-wacom? This confuses me a great deal.

---

### Post by Favux on 2010-08-17
I linked you to it in the Bamboo P&T HOW TO.  That's II., cloning the git, and it is at the linuxwacom site along with the xf86-input-wacom tars.

Linuxwacom has the wacom.ko, the usb kernel driver, and the X driver wacom_drv.so.

Xorg's xf86-input-wacom just supplies the X driver, wacom_drv.so, for Xservers 1.7 and higher.  Linuxwacom's X driver only works for Xservers less than 1.7.

More explanations available at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by s3a on 2010-08-17
I somewhat understand what I did but I would like to understand more later but before I go into that, when I use the tablet whether it be in Lenny (with the 2.6.32 kernel) or in Squeeze, I sometimes find it hard to move the cursor as in it doesn't follow me perfectly like I remember my previous tablet doing. Do you have any ideas as to what's wrong? Do you think it's software-related?

---

### Post by s3a on 2010-08-17
Actually, to be more precise; for me to be able to reach the whole computer screen with the tablet, I need to pull the cursor to the bottom right to reach the top left for example. So, it does sound like a software issue after all. But, I still do not know what to do about it.

---

### Post by Favux on 2010-08-17
OK, so the tablet is working now?

It sounds like you may need to calibrate your Bamboo Pen.  Set up the sample .xsetwacom.sh  to run at startup.  Use only the stylus section, you can delete the other three.  There are settings you can adjust.

The TX2000 .xsetwacom.sh shows you how to put coordinates in.  In Xorg.0.log in /var/log you should see approximate coordinates when the wacom driver initializes the tablet.

---

### Post by s3a on 2010-08-18
Yes, it is working! :) (Thanks)

_I downloaded the tar archive that has the following files:_
Favux_wacom.conf-.xsetwacom.sh
Favux_xorg.conf-.xsetwacom.sh

Before proceeding, do I need both or just one of the two?

---

### Post by Favux on 2010-08-18
They're essentially identical.  The difference is what the "Device names" are in the xsetwaom commands.  Since you're using the 10-wacom.conf you want the wacom.conf one.  You can use either the "Device name" or ID # from 'xinput --list'.  Since the ID # can change with hot plugging, if you're going to hot plug use the "Device name" in the commands.

---

### Post by s3a on 2010-08-18
What's 10-wacom.conf ?

_For the script: (I know you want me to make it run at boot but for me to do that I need to see if it runs well the first time - and it doesn't)_
```
deniz@debian:~$ cd Desktop
deniz@debian:~/Desktop$ chmod +x Favux_wacom.conf-.xsetwacom.sh
deniz@debian:~/Desktop$ sh Favux_wacom.conf-.xsetwacom.sh
Property for 'Suppress' not available.
Property for 'RawSample' not available.
Property for 'ClickForce' not available.
Property for 'PressCurve' not available.
Property for 'TPCButton' not available.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Serial number of failed request:  15
  Current serial number in output stream:  15
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  28 (X_GetDeviceButtonMapping)
  Serial number of failed request:  15
  Current serial number in output stream:  15
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  28 (X_GetDeviceButtonMapping)
  Serial number of failed request:  15
  Current serial number in output stream:  15
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  28 (X_GetDeviceButtonMapping)
  Serial number of failed request:  15
  Current serial number in output stream:  15
Property for 'Suppress' not available.
Property for 'RawSample' not available.
Property for 'ClickForce' not available.
Property for 'PressCurve' not available.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Serial number of failed request:  15
  Current serial number in output stream:  15
Property for 'Touch' not available.
Unknown parameter name 'Gesture'.
Unknown parameter name 'ZoomDistance'.
Unknown parameter name 'ScrollDistance'.
Unknown parameter name 'TapTime'.
deniz@debian:~/Desktop$
```

As for the Xorg.0.log, I don't understand exactly what you want me to do. Are you saying you want me to take something from the script and paste in in xorg.conf or Xorg.0.log?

---

### Post by Favux on 2010-08-18
I think you're over thinking things.

Show me your 'xinput --list' output.

---

### Post by s3a on 2010-08-18
_I removed my mouse to connect the tablet that's why it's not listed (the listed Logitech mouse is broken but is listed because the adapter is a 2 in 1 keyboard/mouse adapter - just saying):_

```
deniz@debian:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImExPS/2 Logitech Explorer Mouse        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                 	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen eraser             	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                    	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
deniz@debian:~$
```

---

### Post by Favux on 2010-08-18
Hi s3a,

Your stylus = Wacom Bamboo 4x5 Pen

Your tablet doesn't have the other two devices:
Wacom Bamboo 4x5 Finger
Wacom Bamboo 4x5 Pen eraser

Those are just spurious entries.  So your script would look like this:
```
## Device names and ID numbers from 'xinput --list'.

## stylus = ID 13 = "Wacom Bamboo 4x5 Pen"
xsetwacom set "Wacom Bamboo 4x5 Pen" Suppress "2"  # data trimmed, 0-100
xsetwacom set "Wacom Bamboo 4x5 Pen" RawSample "20"  # default is 4
xsetwacom set "Wacom Bamboo 4x5 Pen" ClickForce "6"  # 1-21
xsetwacom set "Wacom Bamboo 4x5 Pen" PressCurve "5 10 90 95" # default is 0,0,100,100
xsetwacom set "Wacom Bamboo 4x5 Pen" TPCButton "on"
xsetwacom set "Wacom Bamboo 4x5 Pen" Mode "Absolute"  # or Relative
xsetwacom set "Wacom Bamboo 4x5 Pen" Button1 "1"  # left mouse click
xsetwacom set "Wacom Bamboo 4x5 Pen" Button2 "3"  # right mouse click
xsetwacom set "Wacom Bamboo 4x5 Pen" Button3 "2"  # middle mouse click
#xsetwacom set "Wacom Bamboo 4x5 Pen" topy "-101"
#xsetwacom set "Wacom Bamboo 4x5 Pen" topx "66"
#xsetwacom set "Wacom Bamboo 4x5 Pen" bottomy "16630"
#xsetwacom set "Wacom Bamboo 4x5 Pen" bottomx "26416"
```
The coordinates are not for your tablet.  To get coordinates go to the file Xorg.0.log, it will be at /var/log/Xorg.0.log.  Copy the file into gedit and search 'wacom'.  You'll see the wacom driver initializing the tablet devices.  One of the lines will have the coordinates for the stylus, and you can put them in the script.  Then fine tune manually.

10-wacom.conf replaces the 10-linuxwacom.fdi.  You now have udev/xxxx.conf in xorg.conf.d instead of HAL/.fdi for hot plugging.  The .conf files are located at /usr/lib/X11/xorg.conf.d.  Think of the .conf files in xorg.conf.d as extensions to xorg.conf in /etc/X11.

---

### Post by s3a on 2010-08-18
_Here is the part of the Xorg.0.log:_
> (II) config/udev: Adding input device Wacom Bamboo 4x5 Pen (/dev/input/event10)
(**) Wacom Bamboo 4x5 Pen: Applying InputClass "evdev tablet catchall"
(**) Wacom Bamboo 4x5 Pen: Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event10"
(II) Wacom Bamboo 4x5 Pen: type not specified, assuming 'stylus'.
(II) Wacom Bamboo 4x5 Pen: other types will be automatically added.
(**) Wacom Bamboo 4x5 Pen: always reports core events
(II) Wacom Bamboo 4x5 Pen: hotplugging dependent devices.
(**) Option "Device" "/dev/input/event10"
(**) Wacom Bamboo 4x5 Pen eraser: always reports core events
(II) XINPUT: Adding extended input device "Wacom Bamboo 4x5 Pen eraser" (type: ERASER)
(--) Wacom Bamboo 4x5 Pen eraser: using pressure threshold of 27 for button 1
(--) Wacom Bamboo 4x5 Pen eraser: Wacom USB Bamboo tablet speed=38400 maxX=14720 maxY=9200 maxZ=1023 resX=2540 resY=2540  tilt=disabled
(--) Wacom Bamboo 4x5 Pen eraser: top X=0 top Y=0 bottom X=14720 bottom Y=9200 resol X=2540 resol Y=2540
(II) Wacom Bamboo 4x5 Pen: hotplugging completed.
(II) XINPUT: Adding extended input device "Wacom Bamboo 4x5 Pen" (type: STYLUS)
(--) Wacom Bamboo 4x5 Pen: top X=0 top Y=0 bottom X=14720 bottom Y=9200 resol X=2540 resol Y=2540
(II) config/udev: Adding input device Wacom Bamboo 4x5 Pen (/dev/input/mouse6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Wacom Bamboo 4x5 Finger (/dev/input/event12)
(**) Wacom Bamboo 4x5 Finger: Applying InputClass "evdev touchpad catchall"
(**) Wacom Bamboo 4x5 Finger: Applying InputClass "Wacom class"
(**) Wacom Bamboo 4x5 Finger: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event12"
(II) Wacom Bamboo 4x5 Finger: x-axis range 0 - 480
(II) Wacom Bamboo 4x5 Finger: y-axis range 0 - 320
(II) Wacom Bamboo 4x5 Finger: pressure range 0 - 1023
(II) Wacom Bamboo 4x5 Finger: finger width range 0 - 0
(II) Wacom Bamboo 4x5 Finger: buttons: double triple
(--) Wacom Bamboo 4x5 Finger: touchpad found
(**) Wacom Bamboo 4x5 Finger: always reports core events
(II) XINPUT: Adding extended input device "Wacom Bamboo 4x5 Finger" (type: TOUCHPAD)
(**) Wacom Bamboo 4x5 Finger: (accel) keeping acceleration scheme 1
(**) Wacom Bamboo 4x5 Finger: (accel) acceleration profile 0
(**) Wacom Bamboo 4x5 Finger: (accel) acceleration factor: 2.000
(**) Wacom Bamboo 4x5 Finger: (accel) acceleration threshold: 4
(--) Wacom Bamboo 4x5 Finger: touchpad found
(II) config/udev: Adding input device Wacom Bamboo 4x5 Finger (/dev/input/mouse7)
(**) Wacom Bamboo 4x5 Finger: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
Wacom Bamboo 4x5 Finger no synaptics event device found
(**) Option "Device" "/dev/input/mouse7"
Query no Synaptics: 6003C8
(--) Wacom Bamboo 4x5 Finger: no supported touchpad found
(EE) Wacom Bamboo 4x5 Finger Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Wacom Bamboo 4x5 Finger"

What are the coordinates? Also, I don't know how to set up the script and fine tune it, etc so could you please tell me how to do it in newbie steps? What is 10-wacom.conf and 10-linuxwacom.fdi? When you said that the .conf files are extensions, does that apply to 10-wacom.conf as well or just what's in /usr/lib/X11/xorg.conf.d?

---

### Post by Favux on 2010-08-18
The stylus coordinates are in this line:
```
(--) Wacom Bamboo 4x5 Pen: top X=0 top Y=0 bottom X=14720 bottom Y=9200 resol X=2540 resol Y=2540
```
So the coordinates in the example script I showed you change to:
```
xsetwacom set "Wacom Bamboo 4x5 Pen" topy "0"
xsetwacom set "Wacom Bamboo 4x5 Pen" topx "0"
xsetwacom set "Wacom Bamboo 4x5 Pen" bottomy "9200"
xsetwacom set "Wacom Bamboo 4x5 Pen" bottomx "14720"
```
for your tablet.  Then to fine tune, if needed, just vary the coordinates by 100 or 50 or 10 or whatever and rerun the script until you zero in on what you want.
> Also, I don't know how to set up the script
See IV. in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

> What is 10-wacom.conf and 10-linuxwacom.fdi? When you said that the .conf files are extensions, does that apply to 10-wacom.conf as well or just what's in /usr/lib/X11/xorg.conf.d?
Try reading through III. in the Bamboo P&T HOW TO and also Section 3 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by s3a on 2010-08-19
I tried it on my Debian Squeeze computer so far and it works almost perfectly. So, this is where the fine tuning comes into play so. It's late here so I'll report tomorrow on the situation but things are looking good :)

Edit: Just a question; why must this be done manually? My previous tablet was auto-calibrated perfectly. Also what *exactly* do the numbers mean?:

```
xsetwacom set "Wacom Bamboo 4x5 Pen" topy "**0**"
xsetwacom set "Wacom Bamboo 4x5 Pen" topx "**0**"
xsetwacom set "Wacom Bamboo 4x5 Pen" bottomy "**9200**"
xsetwacom set "Wacom Bamboo 4x5 Pen" bottomx "**14720**"
```

---

### Post by Favux on 2010-08-19
Hi s3a,

> I tried it on my Debian Squeeze computer so far and it works almost perfectly.
Good!
> why must this be done manually? Also what exactly do the numbers mean?
Since linuxwacom's wacomcpl (Wacom Control Panel) isn't available for Xorg's xf86-input-wacom we don't have the calibration feature of wacomcpl available.  And we're using the .xsetwacom.sh script in place of the .xinitrc xsetwacom script that wacomcpl automatically generates.  The numbers reflect the tablet's digitizer grid.

Remember you don't have to restart after changes to the coordinates, just rerun the .xsetwacom.sh and the changes will be applied.

---

### Post by s3a on 2010-08-19
Will Xorg's xf86-input-wacom driver eventually have wacomcpl available to it in the future? As for the script, I made GNOME run the script in the background automatically when I log in. Also, for the tablet's digitizer grid, I wanted to know what effect the numbers have. Like if I increase or decrease each one of the four numbers what effect does it have for each setting? Does a larger number mean that being further from the tablet's limits IS on the monitor's limits? (sorry if that sounds stupid)

---

### Post by Favux on 2010-08-19
> Will Xorg's xf86-input-wacom driver eventually have wacomcpl available to it in the future?
They were hoping for a volunteer to split wacomcpl out and make it a stand alone app. for both linuxwacom and xf86-input-wacom.  So far no voluteer I've heard of, although I've heard rumors.

0,0 is the top left corner.  Then bottom X is the "distance" to the right edge and Bottom Y is the distance to the bottom edge.  You're trying to map the cursor so it will just touch all four corners.  If your monitor is not the same proportion as the tablet you can use the KeepShape option to preserve the tablet's ration, losing some screen room.  There's also a new xsetwacom parameter we could try.

---

### Post by s3a on 2010-08-21
My screen's resolution is 1680x1050 and if the top left corner is 0,0 then shouldn't that mean that my bottom x and bottom y should be 1680 and 1050 respectively?

---

### Post by Favux on 2010-08-21
The digitizer is not the same as your LCD.  The digitizer is basically a grid (think screen door) sandwiched to your LCD.  On your spec.s you might see the digitizer resolution.

---

### Post by Favux on 2010-08-21
The digitizer is not the same as your LCD.  The digitizer is basically a grid (think screen door) sandwiched to the LCD in a tablet pc and in a tablet to the tablet surface.  On your spec.s you might see the digitizer resolution.

---

### Post by s3a on 2010-08-21
What specs? Where do I look?

---

### Post by Favux on 2010-08-21
Should be in the literature or disks that came with it.  We already know what the wacom driver thinks you have:
```
(--) Wacom Bamboo 4x5 Pen: top X=0 top Y=0 bottom X=14720 bottom Y=9200 resol X=2540 resol Y=2540
```
It says resolution X=2540 resolution Y=2540.  Which doesn't sound quite right since the tablet isn't square.

---

### Post by s3a on 2010-08-26
Doing cat /var/log/Xorg.0.log does not return anything with the word wacom in it on my Lenny computer even though the tablet technically works. Also the script only works in Squeeze and not Lenny and I am assuming that I did something Lucid/Squeeze-specific for this to be the case.

---

### Post by Favux on 2010-08-26
I think Lenny still uses HAL?  If so then you have linuxwacom, not the linuxwacom wacom.ko + xf86-input-wacom.  In which case you use 'wacomcpl' to configure.  Enter it into a terminal and the gui should pop up.

---

### Post by s3a on 2010-08-26
Ok I'll try it later but about HAL. I thought HAL was a **newly conceived** tool; why is it being deprecated? Or what else is going on?

---

### Post by s3a on 2010-08-26
I tried it (with the tablet connected) and not only does /var/log/Xorg.0.log not detect it but I also get the following (again, the tablet does work and I don't mean like a mouse):

```
deniz@debian:~$ su
Password: 
debian:/home/deniz# wacomcpl
bash: wacomcpl: command not found
debian:/home/deniz# exit
deniz@debian:~$ wacomcpl
bash: wacomcpl: command not found
deniz@debian:~$
```

---

### Post by Favux on 2010-08-26
OK, squeeze is kind of Lucid.  What's Lenny?  Kernel and Xorg versions?  Didn't we set up your older Bamboo in Lenny last year?

---

### Post by s3a on 2010-08-26
Yes, we did set up the older Bamboo up on Lenny last year. Lenny is somewhere between Ubuntu 8.04 - 8.10 if I'm correct. To be more specific:

```
X.Org X Server 1.4.2
2.6.32-bpo.5-amd64
```

Note that the kernel in my Lenny installation is like the one from Lucid or Squeeze.

---

### Post by Favux on 2010-08-26
Alright you probably need the xorg.conf attached to the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  Doesn't sound like Lenny uses HAL and .fdi files with that Xserver.

Have you installed the linuxwacom packages in Lenny?  Since there's no wacomcpl it sounds like at least wacom-tools isn't installed.  In Ubuntu they're xserver-xorg-input-wacom and  wacom-tools.  And what version of linuxwacom are they?

---

### Post by s3a on 2010-08-26
I did not have wacom-tools installed but installing did not allow me to run wacomcpl. I then proceeded to adding your xorg.conf contents to my xorg.conf's existing contents where what your xorg.conf had is below > ### The following is what I pasted from Favux ### (adding your xorg.conf with zero/one lines commented out prevents me from starting GNOME so I relocated the xorg.conf until I get this sorted out):

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
EndSection

### The following is what I pasted from Favux ###

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

##	Set up for the Bamboo's:  Pen & Touch(CTH460), Craft(CTH461),	##
##	and Fun(CTH661)							##
##	Comment (#) out device sections your model doesn't support	##

Section "InputDevice"
	Identifier "stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"Button2"	"2"  # make first button a middle click
	Option		"Button3"	"3"  # make second button a R click
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"		"on"
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom-touch"
	Option		"Type"		"touch"
	Option		"USB"		"on"
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection

Section "InputDevice"
	Identifier	"pad"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom-touch"
	Option		"Type"		"pad"
	Option		"USB"		"on"
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
#	Identifier	"Default Layout"
#	Screen		"Default Screen"
	Identifier	"X.org Configured"
# Comment out unsupported devices
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
#	Inputdevice	"touch"		"SendCoreEvents"
	InputDevice	"pad"
EndSection
```

Running *cat /var/log.Xorg.0.log* does not help however running *lsmod* does list wacom as a loaded kernel module.

---

### Post by Favux on 2010-08-27
The video stuff in the sample xorg.conf are meant as "placeholders".  You're suppose to substitute yours in.  They're almost the same so you have duplicates in essence.  Remove the video sections in the sample:
```
Section "Device"
	Identifier	"Configured Video Device"
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
And:
```
	Identifier	"X.org Configured"

```
may not work with your older Xserver.  Try commenting it out and removing the comments from:
```
	Identifier	"Default Layout"
	Screen		"Default Screen"

```

---

### Post by s3a on 2010-08-27
I changed the xorg.conf as follows but I still can't start GNOME with the settings as such:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
EndSection

### The following is what I pasted from Favux ###

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

##	Set up for the Bamboo's:  Pen & Touch(CTH460), Craft(CTH461),	##
##	and Fun(CTH661)						##
##	Comment (#) out device sections your model doesn't support	##

Section "InputDevice"
	Identifier "stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"Button2"	"2"  # make first button a middle click
	Option		"Button3"	"3"  # make second button a R click
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"		"on"
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom-touch"
	Option		"Type"		"touch"
	Option		"USB"		"on"
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection

Section "InputDevice"
	Identifier	"pad"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom-touch"
	Option		"Type"		"pad"
	Option		"USB"		"on"
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection



Section "ServerLayout"
	Identifier	"Default Layout" # Favux said to remove the comment from here
	Screen		"Default Screen" # Favux said to remove the comment from here
	Identifier	"X.org Configured" #Favux said to comment this out because the Xorg server is old in Lenny
# Comment out unsupported devices
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
#	Inputdevice	"touch"		"SendCoreEvents"
	InputDevice	"pad"
EndSection
```

---

### Post by Favux on 2010-08-27
This isn't commented out:
```
	Identifier	"X.org Configured" #Favux said to comment this out because the Xorg server is old in Lenny

```
This is now commented out:
```
#	Identifier	"X.org Configured" #Favux said to comment this out because the Xorg server is old in Lenny

```

---

### Post by s3a on 2010-08-28
Oops, typo. I rebooted and it's perfectly calibrated in Lenny (which is my school laptop)! So to recap, in Lenny, is all we did just edit xorg.conf or was there another step to it? (because I don't remember if the other steps were Squeeze/Lucid-specific)

---

### Post by s3a on 2010-08-28
Ok so I follow part 1 of [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1) and then edit the xorg.conf and that's the super quick summary of all I had to do for getting the tablet working under Lenny?

---

### Post by Favux on 2010-08-28
Hi s3a,

Correct, but in I. you need to do 'sudo make install', before the copy command for the wacom.ko, so that the Xdriver wacom_drv.so from linuxwacom is also installed.  See also Section 1 of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

So it's the same thing as what we did with your original Bamboo except we needed a version of linuxwacom that supports the Bamboo P&T's.

By the way wacomcpl should be working.

---

### Post by s3a on 2010-08-28
Something is wrong with what you said. I remember purposely avoiding *sudo make _install_*. Also, wacomcpl does not work, could it be because I did not do *sudo make install* for linuxwacom?

---

### Post by Favux on 2010-08-28
Could be because wacomcpl should be working.  I find it hard to believe that the 0.8.8-8 wacom.ko is even working with whatever old version of the linuxwacom X driver that comes with Lenny.

---

### Post by s3a on 2010-08-30
I'm having trouble with calibration again and I didn't change anything. Could you ask me what I have to check again please?

---

### Post by Favux on 2010-08-30
The wacomcpl gui has a calibration routine.

---

### Post by s3a on 2010-08-30
But, I can't even run wacomcpl! :( (I tried both user and root)

Edit: I forgot to ask what I need to check to diagnose my current problem(s).

Edit #2: It's not installed: ```
deniz@debian:~$ locate wacomcpl
/home/deniz/Desktop/linuxwacom-0.8.8-8/prebuilt/32/wacomcpl
/home/deniz/Desktop/linuxwacom-0.8.8-8/prebuilt/32/wacomcpl-exec
/home/deniz/Desktop/linuxwacom-0.8.8-8/prebuilt/64/wacomcpl
/home/deniz/Desktop/linuxwacom-0.8.8-8/prebuilt/64/wacomcpl-exec
/home/deniz/Desktop/linuxwacom-0.8.8-8/src/wacomxi/wacomcpl
/home/deniz/Desktop/linuxwacom-0.8.8-8/src/wacomxi/wacomcpl-exec
/home/deniz/Desktop/linuxwacom-0.8.8-8/src/wacomxi/wacomcpl.in
deniz@debian:~$
```

I don't want to sudo make install it so can you teach me how to edit the debian files after running dh_make so that I can cleanly install .deb files? Once the code is fully debianized, I can go from there easily.

---

### Post by s3a on 2010-09-01
Also, would having wacomcpl (from the linuxwacom package?) be the solution to my calibration issue?

---

### Post by s3a on 2010-09-04
I also tried the sudo make install for linuxwacom and it worked after a reboot but then, I don't know why, it just stopped working again!

---

### Post by s3a on 2010-09-07
Did you give up on me by any chance? :( Or are you just busy or something?

---

### Post by Favux on 2010-09-07
Hi s3a,

Well kind of busy and the holiday and all.

Besides it seemed like you were posting general observations and kvetching.

Between the thread last year and this one it seems like you have all the links and answers you need to get it working.  So what's wrong?  With a little detail.

---

### Post by s3a on 2010-09-18
Ok I had removed the xorg.conf but now in an attempt to find the issue, I think I have found it (and a workaround so that I can use it). But if you know what's wrong for a permanent fix, then I'd much rather that.

What I did that makes it work:
_xorg.conf:_
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
EndSection

### The following is what I pasted from Favux ###

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

##	Set up for the Bamboo's:  Pen & Touch(CTH460), Craft(CTH461),	##
##	and Fun(CTH661)							##
##	Comment (#) out device sections your model doesn't support	##

Section "InputDevice"
	Identifier "stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"Button2"	"2"  # make first button a middle click
	Option		"Button3"	"3"  # make second button a R click
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"		"on"
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom-touch" # used to be /dev/input/wacom-touch #Favux didn't tell me to do this!!!
	Option		"Type"		"pen" #used to be touch inside the quotes #Favux didn't tell me to do this!!!
	Option		"USB"		"on"
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection

Section "InputDevice"
	Identifier	"pad"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom-touch"
	Option		"Type"		"pad"
	Option		"USB"		"on"
# remove comment below if investigating this device
#        Option		"DebugLevel"	"12" # gives info. for Xorg.0.log
EndSection



Section "ServerLayout"
	Identifier	"Default Layout" # Favux said to remove the comment from here
	Screen		"Default Screen" # Favux said to remove the comment from here
#	Identifier	"X.org Configured" #Favux said to comment this out because the Xorg server is old in Lenny
# Comment out unsupported devices
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
#	Inputdevice	"touch"		"SendCoreEvents"
	InputDevice	"pad"
EndSection

```

Then I did sudo wacomcpl, chose stylus (out of stylus and eraser), then chose tracking, and then slided the top x and top y sliders to the absolute left. Every time I want to use my tablet, I have to do sudo wacomcpl and slide the things left and then reboot so that it works. But then when I reboot again, I have to do it the whole sudo wacomcpl and reboot process again.

I am glad I found the pattern because I can now do homework live with people. Earlier I didn't have wacomcpl. Did I get wacomcpl by installing linuxwacom?

But the final question I have is:
Do I take the script you gave me before:
```
## Device names and ID numbers from 'xinput --list'.

## stylus = ID 13 = "Wacom Bamboo 4x5 Pen"
xsetwacom set "Wacom Bamboo 4x5 Pen" Suppress "2"  # data trimmed, 0-100
xsetwacom set "Wacom Bamboo 4x5 Pen" RawSample "20"  # default is 4
xsetwacom set "Wacom Bamboo 4x5 Pen" ClickForce "6"  # 1-21
xsetwacom set "Wacom Bamboo 4x5 Pen" PressCurve "5 10 90 95" # default is 0,0,100,100
xsetwacom set "Wacom Bamboo 4x5 Pen" TPCButton "on"
xsetwacom set "Wacom Bamboo 4x5 Pen" Mode "Absolute"  # or Relative
xsetwacom set "Wacom Bamboo 4x5 Pen" Button1 "1"  # left mouse click
xsetwacom set "Wacom Bamboo 4x5 Pen" Button2 "3"  # right mouse click
xsetwacom set "Wacom Bamboo 4x5 Pen" Button3 "2"  # middle mouse click

xsetwacom set "Wacom Bamboo 4x5 Pen" topy "500"
xsetwacom set "Wacom Bamboo 4x5 Pen" topx "-1000"
xsetwacom set "Wacom Bamboo 4x5 Pen" bottomy "8800"
xsetwacom set "Wacom Bamboo 4x5 Pen" bottomx "15000"

#xsetwacom set "Wacom Bamboo 4x5 Pen" topy "0"
#xsetwacom set "Wacom Bamboo 4x5 Pen" topx "0"
#xsetwacom set "Wacom Bamboo 4x5 Pen" bottomy "9200"
#xsetwacom set "Wacom Bamboo 4x5 Pen" bottomx "14720"
```

and make it run in the background every single time my computer boots? (by changing the numerical values of topy, topx, bottomy, and bottomx to the values set graphically by wacomcpl?)

---

### Post by s3a on 2010-09-18
Actually, I did just that and it seems to work at every single reboot. I tried rebooting like 5 times or so to see and it works like a charm. I'll report in a few days if there are problems or not.

---

### Post by Favux on 2010-09-18
Hi s3a,

Looking good!

> Did I get wacomcpl by installing linuxwacom?
Yes.
> Do I take the script you gave me before and make it run in the background every single time my computer boots?
As you found out that works.  But .xsetwacom.sh is an imitation of wacomcpl's .xinitrc, because wacomcpl isn't available in Lucid with xf86-input-wacom.  You should be able to set up the .xinitrc to apply each time you boot just like .xsetwacom.sh.  The instructions are the same, but just in case see Section 4 at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

