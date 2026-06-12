---
title: "Ubuntu 10.04: Calibrate touch in HP tx2000"
date: 2010-05-05
forum: General Help
---

### Post by trx64 on 2010-05-05
I have an HP Pavilion tx2000 tablet, wich is working perfectly in Ubuntu 10.04. The touch and the stylus works out of box, and i'm using the script that Favux has posted to rotate my screen and i've installed the wacomrotate daemon, wich is working too.

Now, I've two questions:

- How to calibrate it? The stylus is ok, but the touch isn't calibrated. In Karmic, I was using wacomcpl and xsetwacom, but neither of them detect my tablet now (in 9.10, Hal was used to detect the tablet, now it's xserver-xorg-input-wacom).
```
leotorok@leotorok-laptop:~$ xsetwacom set touch bottomy "3932"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'touch'
leotorok@leotorok-laptop:~$ 
```

- It's possible to set up the automatic screen rotation, like in Windows (the screen rotates automaticaly in tablet position)?

---

### Post by dino99 on 2010-05-05
xserver-xorg-input-wacom installed ?

[http://ubuntuforums.org/showthread.php?p=9177144](http://ubuntuforums.org/showthread.php?p=9177144)

---

### Post by trx64 on 2010-05-05
Yes, it's installed, and the tablet and stylus are working. The problem is how to calibrate the touch and how to change the second button of the stylus (it's set to middle click, not right click):

```

 leotorok@leotorok-laptop:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                              id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 eraser                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                              id=13    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
leotorok@leotorok-laptop:~$ xsetwacom set 12 Button3 "2"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
leotorok@leotorok-laptop:~$ xsetwacom set 13 Button3 "2"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
leotorok@leotorok-laptop:~$ xsetwacom set "Wacom ISDv4 93" Button3 "2"
X Error: 2 BadValue (integer parameter out of range for operation)
Error (22): WacomConfigSetRawParam: failed
Set: Failed to set Wacom ISDv4 93 value for 'Button3'
leotorok@leotorok-laptop:~$ xsetwacom set "Wacom ISDv4" Button3 "2"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Wacom ISDv4'
leotorok@leotorok-laptop:~$ 

```

---

### Post by Favux on 2010-05-05
Hi trx64,

My calibration is:
```
xsetwacom set touch bottomy "3969"
xsetwacom set touch bottomx "4028"
xsetwacom set touch topy "215"
xsetwacom set touch topx "140"
```
Your xinput list is giving the same Device name for stylus and touch.  That might actually be a bug.  The touch device should be labled with touch I think.  But instead of just the "device name" in quotes you can also use the ID number.  Let's guess touch is 13.  So it would look like:
```
xsetwacom set 13 bottomy "3969"
xsetwacom set 13 bottomx "4028"
xsetwacom set 13 topy "215"
xsetwacom set 13 topx "140"
```
Put it in a script say .xsetwacom.sh (to replace wacomcpl's .xinitrc), make it executable, and set it up to auto-start with the session.

---

### Post by trx64 on 2010-05-05
Thanks by the answers, Favux and dino99. I've tryed to set it with xsetwacom, but:
```

leotorok@leotorok-laptop:~$ xsetwacom set 13 bottomy "3969"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
leotorok@leotorok-laptop:~$ xsetwacom set touch bottomy "3969"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'touch'
leotorok@leotorok-laptop:~$ xsetwacom set 13 topy "215"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
leotorok@leotorok-laptop:~$ xsetwacom set 12 topy "215"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
leotorok@leotorok-laptop:~$ 

```

It's possible to change directly the file /usr/lib/X11/xorg.conf.d/10-wacom.conf to change the settings? It will be added to xorg.conf and X.org is handling the wacom tablets now.

My 10-wacom.conf:
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

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

```

---

### Post by Favux on 2010-05-05
Hi trx64,

Maybe I guessed wrong and touch is 12?  Let's look at what:
```
xsetwacom list
```
shows.

You should be able to add the coordinates to the wacom.conf, but at least one person who tried it said it didn't work.  Another said coordinates work if you use the location they recommend for custon changes, which I believe is /etc/X11/xorg.conf.d/.

---

### Post by trx64 on 2010-05-05
"xsetwacom list" doesn't show any devices:
```

leotorok@leotorok-laptop:~$ xsetwacom list
leotorok@leotorok-laptop:~$ 

```

What changes should I do in 10-wacom.conf to calibrate the touch and change the button of the stylus?

---

### Post by Favux on 2010-05-05
Hi trx64,

Apparently you can use the same syntax as for options in xorg.conf.  There also may be a alternate sytax we could try if the coordinate options don't work.
```
Option "Button2" "3"

Option "bottomy" "3969"
```
You would add it to the bottom of the usb snippet which has the identifier:
```
Identifier "Wacom class"

```

---

### Post by trx64 on 2010-05-06
Favux, I've made the changes (using the values of xinitrc, wich was ok in Karmic). The touch is calibrated, but now the stylus wasn't calibrated (before that, the touchscreen was 1cm out of place. After that, the stylus is 20 cm out of the place :D).

The option to change the button worked perfectly. Here's my new 10-wacom.conf (I've commented the lines about the position):
```

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
#    Option "bottomy" "3932"
#    Option "bottomx" "3984"
#    Option "topy" "187"
#    Option "topx" "139"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection


```

---

### Post by Favux on 2010-05-06
Hi trx64,

> I've made the changes (using the values of xinitrc, wich was ok in Karmic). The touch is calibrated, but now the stylus wasn't calibrated (before that, the touchscreen was 1cm out of place. After that, the stylus is 20 cm out of the place ).
Well of course.  I feel a little silly.  The usb section is everything so we need a "match" line that seperates out touch and then we should list the touch coordinates below that!  Something like:
```
ENV{ID_INPUT_TOUCH}==1
```
We'll have to look at your udevadm info and look up the device tree for touch for the appropriate match line:
```
udevadm info --export-db > $HOME/udevadm.txt
```

I suppose the alternative would be to add a touch section with coordinates in xorg.conf.

---

### Post by trx64 on 2010-05-07
I've used the command that you posted. The file is a too big to be posted, so it's attached in my post.

---

### Post by Favux on 2010-05-07
Hi trx64,

OK, here's the third section up the touch branch:
```
P: /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.3/1-2.3:1.1/input/input8/event8
N: input/event8
S: input/tablet-tpc93-touch
S: input/wacom-touch
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.3/1-2.3:1.1/input/input8/event8
E: MAJOR=13
E: MINOR=72
E: DEVNAME=/dev/input/event8
E: SUBSYSTEM=input
E: ID_INPUT=1
E: ID_INPUT_TOUCHSCREEN=1
E: ID_VENDOR=Tablet
E: ID_VENDOR_ENC=Tablet
E: ID_VENDOR_ID=056a
E: ID_MODEL=ISD-V4
E: ID_MODEL_ENC=ISD-V4
E: ID_MODEL_ID=0093
E: ID_REVISION=0244
E: ID_SERIAL=Tablet_ISD-V4
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030102:030000:
E: ID_USB_INTERFACE_NUM=01
E: ID_USB_DRIVER=wacom
E: ID_PATH=pci-0000:00:0b.1-usb-0:2.3:1.1
E: WACOM_TYPE=touch
E: DEVLINKS=/dev/input/tablet-tpc93-touch /dev/input/wacom-touch
```
You can see I almost guessed right.  So something like:
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
    ENV{ID_INPUT_TOUCHSCREEN}==1
      Option "bottomy" "3932"
      Option "bottomx" "3984"
      Option "topy" "187"
      Option "topx" "139"
EndSection
```
Remember to back up your current working 10-wacom.conf and be prepared to restore it from the command line in case we break X.

---

### Post by trx64 on 2010-05-07
Hi, Favux. The change left X.org broken, the message in the console said that the line:

Isn't valid. I've restored the backup of the file and X is up now (of course, with the touch still not calibrated).

Now I've founded something interesting in Xorg.0.log. The lines in bold show that X is detecting the stylus, touch and eraser (what's the eraser in the tablet? How i use that?). The touch and the stylus are detected with the same name, and are calibrated with the same values.

```

(II) config/udev: Adding input device Wacom ISDv4 93 (/dev/input/event8)
(**) Wacom ISDv4 93: Applying InputClass "evdev tablet catchall"
(**) Wacom ISDv4 93: Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.10.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event8"
(II) Wacom ISDv4 93: type not specified, assuming 'stylus'.
(II) Wacom ISDv4 93: other types will be automatically added.
(**) Wacom ISDv4 93: always reports core events
(**) Option "Button2" "3"
(II) Wacom ISDv4 93: hotplugging dependent devices.
(**) Option "Device" "/dev/input/event8"
(**) Wacom ISDv4 93 eraser: always reports core events
(**) Option "Button2" "3"
**(II) XINPUT: Adding extended input device "Wacom ISDv4 93 eraser" (type: ERASER)**
(--) Wacom ISDv4 93 eraser: using pressure threshold of 15 for button 1
(--) Wacom ISDv4 93 eraser: Wacom USB TabletPC tablet speed=38400 maxX=26312 maxY=16520 maxZ=255 resX=2540 resY=2540  tilt=disabled
(--) Wacom ISDv4 93 eraser: top X=0 top Y=0 bottom X=26312 bottom Y=16520 resol X=2540 resol Y=2540
(II) Wacom ISDv4 93: hotplugging completed.
**(II) XINPUT: Adding extended input device "Wacom ISDv4 93" (type: STYLUS)**
(--) Wacom ISDv4 93: top X=0 top Y=0 bottom X=26312 bottom Y=16520 resol X=2540 resol Y=2540
(II) config/udev: Adding input device Wacom ISDv4 93 (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Wacom ISDv4 93 (/dev/input/event10)
(**) Wacom ISDv4 93: Applying InputClass "evdev touchscreen catchall"
(**) Wacom ISDv4 93: Applying InputClass "Wacom class"
(**) Option "Device" "/dev/input/event10"
(II) Wacom ISDv4 93: type not specified, assuming 'touch'.
(II) Wacom ISDv4 93: other types will be automatically added.
(**) Wacom ISDv4 93: always reports core events
(**) Option "Button2" "3"
(II) Wacom ISDv4 93: hotplugging dependent devices.
(II) Wacom ISDv4 93: hotplugging completed.
**(II) XINPUT: Adding extended input device "Wacom ISDv4 93" (type: TOUCH)**
(--) Wacom ISDv4 93: using pressure threshold of 15 for button 1
(--) Wacom ISDv4 93: Wacom USB TabletPC tablet speed=38400 maxX=0 maxY=0 maxZ=255 resX=2540 resY=2540  tilt=disabled
(--) Wacom ISDv4 93: top X=0 top Y=0 bottom X=4095 bottom Y=4095 resol X=2540 resol Y=2540
(II) config/udev: Adding input device Wacom ISDv4 93 (/dev/input/mouse3)

```

---

### Post by Favux on 2010-05-07
Alright.
```
ENV{ID_INPUT_TOUCHSCREEN}==1

```
Is syntax for rules.d upstream.  I was hoping/wondering if it would work.  Ok if the stylus/eraser are on "/dev/input/event8" 
then it looks like touch is on "/dev/input/event10"?  So then:
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchVendor "56a"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
    MatchDevicePath "/dev/input/event10"
      Option "bottomy" "3932"
      Option "bottomx" "3984"
      Option "topy" "187"
      Option "topx" "139"
EndSection
```
The eraser should be on the back of the stylus just like a pencil and depresses into the stylus.  You can use it in programs set up for it like Gimp, Inkscape, and Xournal, etc..

---

### Post by daulpavis on 2010-07-04
Hi

Im running the tx2000 on 10.04 as well.

Did you come to any conclusion on how to calibrate the touch without destroying the pen calibration?

Cheers

---

### Post by Favux on 2010-07-04
Yes, the best way is setting up a xsetwacom script like wacomcpl's .xinitrc.  Let's make one for the TX200.  What is the output of:
```
xinput --list
```
for your TX2000?

---

### Post by daulpavis on 2010-07-06
Output is:

```
paul@paul-laptop:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

```

I attempted editing the 10-wacom.conf file with the same result, the touch calibrated but the pen then was completely off. 

cheers for the help

---

### Post by Favux on 2010-07-06
Another mystery appears.  Where is your eraser?  It probably should look something like "Wacom ISDv4 eraser".

It looks like you have the default 0.8.4-4 wacom.ko and it has a bug and gives the stylus and touch the same name, "Wacom ISDv4 93".  So we have to figure which ID number is which.  We want to identify the ID number that turns off touch.  In a terminal enter:
```
xsetwacom set 11 Touch "on"
```
or
```
xsetwacom set 12 Touch "on"
```

To turn touch back on:
```
xsetwacom set ? Touch "on"
```

---

### Post by daulpavis on 2010-07-06
Okay, I had something I tried in the config which screwed with it a bit. Its back to how it should be and here is the output:

```

paul@paul-laptop:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 eraser                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=13	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
paul@paul-laptop:~$ xsetwacom list
Wacom ISDv4 93 eraser ERASER    
Wacom ISDv4 93   STYLUS    
Wacom ISDv4 93   TOUCH     

```

The ID of the touch is 13

Where do I go from there?

thanks

---

### Post by Favux on 2010-07-06
OK, try this script.

Use IV. here:  [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)  to set the script up.

---

### Post by daulpavis on 2010-07-06
Awesome. Thanks alot.

---

### Post by Favux on 2010-07-06
You're welcome.  Sounds like they're working for you.  Remember if you want to fine tune them you can just enter the xsetwacom command with the coordinate change in a terminal and it takes immediate effect.  That makes manual tuning less of a pain.

---

### Post by Vermilion Sparrow on 2010-08-20
I'm helping my brother set up his HP tx2000, and before I installed the script, touch and stylus were calibrated reasonably well without my having changed any settings, but pressure and the stylus buttons weren't working. On just running the script file I got a cascade of error messages, but despite this, the stylus buttons and pressure started working:

```
a10cwarhog@Noir:~$ /home/a10cwarhog/.xsetwacom.sh
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '12'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '11'
Set: Unknown parameter 'Touch'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
Set: Unknown parameter 'TapTime'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'

```

What is baffling me is this: the touch calibration, which was fine before, is now very strange. If I put my finger at the top of the screen, the cursor is about half a inch below my finger. If I put my finger an inch and a half above the bottom of the screen, the tip of the cursor is barely visible off the bottom edge. If I move my finger up and down on the screen, the cursor gets farther from my finger as I move down the screen, and closer as I move up. I've tried to change the settings, but changing the numbers appears to do nothing (same error message).

```
a10cwarhog@Noir:~$ xsetwacom set 13 bottomy "4322"
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device '13'
```

Stylus calibration, if anything, is a bit tighter than it was before. I did reboot (without the script running at startup) but the touch behavior didn't go back to the way it was before, so I really have no idea what is going on here.

This is the same as other output in the thread, but I know someone will ask:
```
a10cwarhog@Noir:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 eraser                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=13	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
```

---

### Post by Favux on 2010-08-20
Hi Vermilion Sparrow,

Not clear what's going on.  It seems xsetwacom isn't installed correctly.  You can go to Synaptic Package Manager and tell it to reinstall xserver-xorg-input-wacom and reboot.  See if that clears it up.

If not you'll have to update linuxwacom and xf86-input-wacom.  See I. and II. in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") or Sections 1 and 2 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  The bonus is you'll lose the bug in default 0.8.4-4 wacom.ko that calls the stylus and touch the same name.

Linuxwacom is probably not running touch anymore, it's probably the evdev driver or the Synaptic driver.  You could look at Xorg.0.log in /var/log to check.

---

### Post by Vermilion Sparrow on 2010-08-21
Thanks, I removed linuxwacom and installed the latest version and it seems to be behaving properly now. Not sure what was going on there.

---

### Post by heinercg on 2011-02-11
Hello everyone...

Anybody could make the button of the stylus works as mouse right-button? I couldn't. Other estrange thing: the command ClickForce is not working for me, I replaced by the word Threshold as I read in a different page, it works with no errors but I don't know what this command is doing.

Thanks in advance.

---

### Post by Favux on 2011-02-11
Hi heinercg,

Welcome to Ubuntu forums!

All you should need to do is determine the stylus "device name" with:
```
xinput list
```
in a terminal and then use it in a xsetwacom command:
```
xsetwacom set "device name" Button2 "3"
```
where 3 is short for button 3, i.e. a right mouse click.  2 is a middle click.

They changed the name a few weeks ago to Threshold.  More name changes are due shortly, so be prepared to use:
```
xsetwacom list param
```
or the get command to find out what they are.  By the way param may be changing to parameter.

Anyway Threshold is how much pressure you have to exert on the stylus tip before a button 1 event (left click, stylus tip by default) is sent.  It's to stop spurious left clicks at very light pressure i.e. unintended.

---

### Post by heinercg on 2011-03-10
Thanks Favaux for your help.

Now I have some problems with calibration after rotating. For rotating I'm using Magick-rotation 1.3 I don't know if you are familiar with that program. But could you help me how to calibrate my stylus, eraser and touch after a rotation. 

Thank you.

---

### Post by Favux on 2011-03-10
Hi heinercg,

I'm somewhat familiar with Magick.  It shouldn't mess up your calibration.  Could you tell me what's happening to the calibration of stylus, eraser, and touch after a rotation?

---

### Post by heinercg on 2011-03-11
The calibration mess up completely, ej: I point the stylus at the centre of the screen but the mouse is at the top of the screen. For your information the only way that I could calibrate my stylus, eraser and touch was making a script with the coordinates*, make it executable and running from start. I wonder if you have the new rotation coordinates in order to run them before the computer rotates. 

Thank you for your support

*By the way, the coordinates script is from you: Favux_TX2000-wacom.conf-.xsetwacom.sh

---

### Post by Favux on 2011-03-11
It sounds like the input tools aren't being rotated back to laptop mode.  Are they 90 degrees out of phase?  If so let's try the simplest thing first.  In Setup (right click on Magick green arrow icon chose Setup) make sure the box in front of "BIOS hinge switch values reversed?" isn't checked.  If it is checked uncheck it and Save.

---

### Post by heinercg on 2011-03-11
I check the box in front of "BIOS hinge switch values reversed" and it isn't checked. What else can I try?

---

### Post by Favux on 2011-03-11
With the box unchecked click on Save.  Let's make sure that's the setting Magick is using.

I suppose it is possible your BIOS values are reversed for some reason.  You have a TX2000 correct?  The check box is for HP Compaq TC4200 & 4400 tablet PCs.

So if the box unchecked doesn't work try checking it and Saving it and let's see what happens.

---

### Post by heinercg on 2011-03-14
Hi Favaux..

I did just what you said and the behaviour is inverted. Checking that option makes my computer rotates the screen when it is normal and when I put my computer in tablet mode the screen becomes normal, it's totally the opposite that it's supposed to do.

Thanks for your help.

---

### Post by Favux on 2011-03-14
That sounds like what should happen when the box is checked.  Is the stylus now in phase or 90 degrees out of phase or what?  OK, so when it is out of whack to begin with it's 180 degrees out of phase?

I suspect you need to reverse cw and ccw in the code.  What kernel and X server version do you have?:
```
Xorg -version
```
Do you have the default Lucid wacom.ko and Wacom X driver (xf86-input-wacom).  Or did you update either or both?  To what version?

---

### Post by heinercg on 2011-03-16
Hi Favaux, I agree with you and I think the calibration is missed by 90 or 180 degrees or something. I just typed the code you gave me and this was the response:

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux heiner-laptop 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-29-generic root=UUID=96a850cb-de71-4765-b016-31ce52f430b2 ro quiet splash
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
#########################################################################

Now, When I installed the xf86-input-wacom I went to the wacom website and installed this: xf86-input-wacom-0.10.10.tar.bz2

For X server I looked for it in synaptic and I found this:
xserver-xorg-input-wacom installed version: 1:0.10.5-0ubuntu4.

I hope this helps... thanks again...

---

### Post by Favux on 2011-03-16
I've forgotten if this is due to a bug in xf86-input-wacom-0.10.5, which is the default in Lucid.  It's the Wacom X driver and is what the package xserver-xorg-input-wacom contains.

Let's see if updating xf86-input-wacom fixes it.  See part II. in the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") to clone the xf86-input-wacom git repository.

---

### Post by heinercg on 2011-03-17
when I paste git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom

I get this:

Initialized empty Git repository in /home/heiner/xf86-input-wacom/.git/
linuxwacom.git.sourceforge.net[0: 216.34.181.91]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)

Do you know what could be the problem?

---

### Post by Favux on 2011-03-17
The Sourceforge download site might be down temporarily.  Try again in a little bit.  It looks like you installed git.

---

