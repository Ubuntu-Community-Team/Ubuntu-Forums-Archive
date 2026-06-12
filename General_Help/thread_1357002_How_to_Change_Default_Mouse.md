---
title: "How to Change Default Mouse"
date: 2009-12-16
forum: General Help
---

### Post by Daddyo-613 on 2009-12-16
I started a thread, [[COLOR="Blue"]Mouse Stops Working - Details[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1355790") but I haven't received any responses.

**The Problem:** Is that the Mouse works on boot up but freezes after a while and will not respond without rebooting.

I'm using a Ms Wireless Laser Mouse 5000 attached to a USB port.

Using Xinput list, I've confirmed that my mouse is identified as id=4 see the output below:
```
stephen@stephen-desktop:~$ xinput list
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Microsoft Microsoft Wireless Optical Mouse? 1.00"	id=4	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

but dmesg |grep mouse reports:```
stephen@stephen-desktop:~$ dmesg | grep mouse
[    1.937422] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.940670] mice: PS/2 mouse device common for all mice
```

When my mouse freezes, as it just has again, I have to reboot to get it back.

What I think is happening is that HAL is not passing on the information about the detected mouse to allow it to be listed as the default device.

I want to see if I can change the default device to id=4 but I have to better understand how HAL passes on the information about the devices it detects.

Any help will be appreciated.

---

### Post by Daddyo-613 on 2009-12-18
Sadly, I haven't got any help from the Ubuntu community on this or my other post linked in my note above. 

My USB mouse continues to freeze periodically during normal use.

I have been scouring this forum and the web looking for clues as to how Ubuntu deals with HID (human input devices) in particular a mouse pointing device.

The output from my Xorg.0.log is below:```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux stephen-desktop 2.6.27-16-generic #1 SMP Tue Dec 1 17:56:54 UTC 2009 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 18 12:14:36 2009
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

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 8400 GS rev 161, Mem @ 0xd2000000/0, 0xc0000000/0, 0xd0000000/0, I/O @ 0x0000a000/0, BIOS @ 0x????????/131072  

**(Note: I have edited out the video entries from the X.org.o.log file to make it a bit shorter for you to read) ...**

(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 2.0.99
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Mouse? 1.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: always reports core events
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: Device: "/dev/input/event2"
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Configuring as mouse
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse? 1.00" (type: MOUSE)
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Fri Dec 18 12:14:42 2009: 5525 X: client 4 rejected from local host ( uid=0 gid=0 pid=5710 )
AUDIT: Fri Dec 18 12:14:49 2009: 5525 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5775 )
AUDIT: Fri Dec 18 12:14:49 2009: 5525 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5776 )
AUDIT: Fri Dec 18 12:14:49 2009: 5525 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5777 )
```What seems to be happening from the Xorg.0.log file is that:

1.  **First**, the O/S looks for default settings in /etc/X11/xorg.conf[FONT=monospace] but doesn't find any settings for a "Configured Mouse" because the the input devices are to be handled by HAL (hardware abstraction laver).

2.  **Second**, the O/S trys to Automatically add and enable devices but no path is specified so in accordance with its prescribed rules it loads the modules in /usr/lib/xorg/modules and attempts to locate a core pointer device but is unable to locate one because "(II) The server relies on HAL to provide the list of input devices." HAL of course hasn't been loaded at this stage so the O/S goes on to deal with video and other devices and presumably loads the PS/2 mouse info referred to the output of dmesg | grep mouse.

3.  **Third** the O/S gives the message "(II) config/hal: Adding input device Macintosh mouse button emulation" and "(II) LoadModule: "evdev" and proceeds to load the drivers [/FONT]in /usr/lib/xorg/modules/input//evdev_drv.so. The drivers it loads are for the Macintosh button emulation from /dev/input/event0".

4.  **Fourth**, the O/S uses XINPUT which I think is part of the "hotplug" protocall this is supposed to allow USB devices to be changed on the fly without having to reboot. HAL detects the mouse that is actually connected to the USB passes that information along to XINPUT which tells the O/S to use /dev/input/event1 which is the actual mouse.

Then why doesn't it work? Crap...it just happened again. I'll do my best to finish this without a functioning mouse...Grrrrr

"xinput list" shows that the Virtual Core Pointer is assigned "id=1"
and that the Macintosh button emulation is assigned "id=2"
and that the AT Translated Set Keyboard is assigned "id=3"
and that the MS Wireless Mouse is assigned "id=4.

This is too irritating...I'm going to have to reboot and I'll come back and edit this...

...

I'm back...I really hope someone will read this and give me some help.

I installed the gnome-device-manager 0.2 and it reports that the Macintosh mouse button emulator is loaded from /dev/input/event0
and that a MS Wireless Optical Mouse? 1.00 is loaded from /dev/input/event/2 but it sets out the hierarchy as follows:

- USB OHCI Controller
   - HUB Model 1.1 root hub
          - Hub interface
       -USB Device Wireless Laser Mouse 6000 Reciever
           - Mouse HID Device Interface (Boot) Interface
               -Pointing Device - Microsoft Microsoft Wireless Optical Mouse? 1.00 from /dev/input/event2

Somehow either the mouse or the USB hub or interface is timing out and the system is defaulting to the Core Pointer Device that is not the mouse I'm using. I have tried changing USB ports. I have tried connecting a standard wired mouse to the PS/2 port and rebooting. I have reloaded the kenel and nothing seems to change. The mouse still freezes after using it for some time.

Well that's all I can thing of at the moment. I hope someone will see this and take pity on me and give me some clues where to look.

P.S. I have seen a large number of postings by others who are having various problems with USB ports and mice but none of the postings I've seen have any solutions.
                                  
       


[FONT=monospace]
[/FONT]

---

### Post by fragos on 2009-12-18
I have multiple cursor control devices connected over USB -- mouse, touchpad and Wacom tablet. Which ever one I use, it automatically takes control of the cursor. I had some Microsoft wireless mouse troubles and just pluged in a 2nd mouse and it worked.

---

### Post by Daddyo-613 on 2009-12-19
Hey somebody is actually trying to help...thank you fragos!

When the mouse froze, I did try to add a second mouse...both to another USB port and using an adapter to the PS/2 port...it didn't help. I tried various combinations of booting. I tried with a standard USB mouse connected in the PS/2 port, the same mouse connected to various USB ports as well as combinations with two pointed devices attached.

On reboot each device would work for a time. When two devices were connected I could even switch devices and they would continue to work as long as I didn't hotplug the wireless mouse but eventually one or the other would crash and then neither would work until I rebooted.

That's why I started to looking at how the devices were handled on bootup so that perhaps I could change the description or the order in which the default devices were loaded.

I've seen some older posts which suggest adding apci=force irqpoll to xorg.conf but they precede the updates incorporating hotpluging, I'm opened to suggestions.

---

### Post by fragos on 2009-12-19
While we're on the subject of flaky mice operation I've also experienced a problem caused by my mouse pad. It was a called a WOW pad and was thin and plastic. The surface had an even texture you could see or feel with your finger. Over time when using my laser mouse the cursor would disappear and wouldn't come back. As an experiment I activated the feature that shows you where the cursor is when you use the Ctrl key. This showed me that the cursor was stuck in a corner. Unplugging the mouse seemed to reset and it would again work. The problem turned out to be the WOW pad whose textured surface was wearing off which confused the laser. I verified the problem by using a clean sheet of white paper as a pad. I went to the plastic pad to avoid another issue that came with a cloth covered pad. The cloth pad would pick up dust which would be deposited inside the port to the LED or laser. In this case the cursor didn't disappear, it froze in position.

---

### Post by Daddyo-613 on 2009-12-20
**fragos**, sorry I've been away from my machine. You know how sometimes real life actually interferes with trying to solve a computing puzzle...I hate that...

Anyway, the problem with the cursor seemingly disappearing is a new one one me. Kudos on figuring that one out. Sadly, that scenario isn't what's happening on my machine. When the mouse freezes, the cursor is still on the screen and very visible. It will even display animations like the "wait" symbols when I execute keyboard commands. I can see it. I just can't move it with the mouse,

If there were some way to reinitialize the mouse without having to reboot, that would be an improvement. I have tried opening a "tty" terminal (for others who may read this <Ctrl>+<Alt>+F2) and trying to restart various elements but I haven't hit upon commands that would reload a mouse. (Note: again for others who may read this...to close the "tty" terminal type "exit" at the $prompt to end your tty session and then press <Ctrl>+<Alt>+F7, that will bring you back to your X session which is your GUI screen.)

Any thoughts?

---

### Post by pbrane on 2009-12-20
I'm sure you have already tried unplugging the USB receiver and plugging it back in. That doesn't work, right? I had wireless mouse issues even on my wifes old windows machine. Thankfully she quit using windows!

Have you tried xinput to disable and enble the mouse?

something like:
**xinput set-int-prop "Microsoft Microsoft Wireless Optical Mouse? 1.00" "Device Enabled" 8 0**
should turn it off, then
**xinput set-int-prop "Microsoft Microsoft Wireless Optical Mouse? 1.00" "Device Enabled" 8 1**
should re-enable it.

Have you considered upgrading to Karmic?

As a side note CTRL-D will close a tty as well.

Is this computer a laptop with a touchpad?

You can list the proerties for your mouse with
**xinput list-props "Microsoft Microsoft Wireless Optical Mouse? 1.00"**
that way you can confirm that the "Device Enabled" parameter is the correct one to use.

---

### Post by fragos on 2009-12-20
I forget to mention that when I had my dust in the optical port problem the cursor position did freeze and I couldn't always see any obstruction but blowing into the port did clear the problem. I can't know if that's your problem but the symptom is the same.

---

### Post by Daddyo-613 on 2009-12-20
Hey thanks for helping...

To respond to pbrane's post:

1.  **Unplugging:** Yes I did try unplugging and replugging the USB wireless transceiver on the fly but it didn't reinitialize the mouse. BTW I'm still trying to wean my household off that other O/S. I've made progress but we're not there yet.

2. **My System **(at the office)**:** is a Desktop PC
CPU: Intel Core 2 Duo E6300 1.86GHz(1066MHz) s775
RAM: Kingston 1GB 240-pin DDR II 533MHz/PC4200
O/S: Ubuntu 8.10 Intrepid
Kernel: 2.6.27.16-Generic
Video Card: Asus GF7300LE w/TurboCache128MB TVOut DVI
Video Driver: nVidia ver. 180
USB Controllers: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 and 20)

Settings Manager: CCSM ver. 0.7.8
Window Manager: Compiz
Window Decoratior: GTK Window Decorator

3.  **Karmic**: I'm using 8.10 because of it's stability (at least up to now). I had instability problems with video when going from Intrepid to Jaunty and had to return to Intrepid to solve issues. I haven't tried Karmic.

2.  **Xinput:** I haven't tried your <xinput> command before but I have been looking at xinput and its options. Unfortunately, the machine I'm having the problem with is at my office and I'm at home now. 

So what I did as a test, was to open a terminal on my machine at home and use <xinput list> to identify the devices enabled on that machine. From the output in the terminal, I found the section that related to my mouse and found the description used by the system to identify my mouse and the id=number assigned to that mouse.```
stephen@stephen-desktop:~$ xinput list
"Virtual core keyboard"    id=0    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Virtual core pointer"    id=1    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is 0
        Max_value is -1
        Resolution is 0
"Macintosh mouse button emulation"    id=2    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"    id=3 [XExtensionPointer]
    Num_buttons is 32
"Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"     Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Microsoft Microsoft? Digital Media Keyboard"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 2
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
    Axis 1 :
        Min_value is 0
        Max_value is 255
        Resolution is 10000
"Microsoft Microsoft? Digital Media Keyboard"    id=5    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255

```I then use <xinput set-init-prop> command to try and turn the mouse attached to my machine at home off. My syntax must be wrong because it didn't seem to do anything. BTW I used xinput --help to list the arguments and options and it appears the command is xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...] and not <xinput set-prop-init> as set out in your post. Not to worry just a typo but if others look at this exchange, they might get confused so I thought I'd mention it.

Anyway when I tried to shut down the mouse this is what I got:```
stephen@stephen-desktop:~$ xinput set-int-prop "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" "Device Enabled" 8 0
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  148 (XInputExtension)
  Minor opcode of failed request:  37 ()
  Value in failed request:  0x5d
  Serial number of failed request:  13
  Current serial number in output stream:  14
``` let me know if I've typed something wrong.

In any event I ran <xinput list-props> to see how my mouse at home was responding and this is what I got:```
stephen@stephen-desktop:~$ xinput list-props "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"
Device 'Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)':
    Device Enabled:        1
    Middle Button Emulation:        2
    Middle Button Timeout:        50
    Wheel Emulation Inertia:        10
    Wheel Emulation:        0
    Wheel Emulation X Axis:        0, 0
    Wheel Emulation Y Axis:        4, 5
    Wheel Emulation Timeout:        200
    Wheel Emulation Button:        4
    Drag Lock Buttons:        0

```What I noticed is that there is output for "Middle Button Timeout" and Wheel Emulation Timeout". I'm wondering if these settings for the mouse at the office might be causing the problem. It would explain why the mouse works on bootup but freezes after a while. Interesting, I'll have to try and figure out just what those settings are doing.

I'll try some of these commands at the office to see if I can re-enable the mouse in a terminal when it freezes without having to reboot.

(**Note:** For others who may be interested you can type <xinput --help> in an opened terminal and get a list of the options and arguments available with this command. You might also want to take a look at this Wiki on xinput [Xorg Input Hotplugging-ArchWiki]("http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#How_can_I_check_if_I.27m_using_the_evdev_driver.3F"))

To respond to fragos "Dust in the USB Port" issue. It seems unlikely that all of the 10 USB ports on my machine would be blocked with dust when they otherwise seem to work with other devices such as an external HD. However, nothing is impossible and I'll try to find a can of compressed air and give the ports a good dusting.

The post is still unresolved but I am grateful for the interest I have received so far. Any suggestions are welcomed at this point.

TTFN

---

### Post by fragos on 2009-12-20
> **Daddyo-613 said:**
> 
To respond to fragos "Dust in the USB Port" issue. It seems unlikely that all of the 10 USB ports on my machine would be blocked with dust when they otherwise seem to work with other devices such as an external HD. However, nothing is impossible and I'll try to find a can of compressed air and give the ports a good dusting.

Sorry for not being more clear, the port I was referring to is the the LED hole in the bottom of the mouse and not the USB ports on your PC.

---

### Post by pbrane on 2009-12-20
Thanks for pointing out that "typo". I wasn't paying attention. I actually had my script open in an editor, you'd think I could at least read it correctly.

That error you got "X Error of failed request:  BadValue (integer parameter out of range for operation)", maybe the integer value is not 8-bit. (That's the '8' in the xinput command). I'm not sure how to discover what the actual format is for an integer value.

Actually I just tried the same command with a '16' parameter when it should be '8' and I got the same "BadValue" error. You should try it with a value of 16 or 32 and see if that is the issue.

The other important thing to note here is that I'm running a newer version of X than you are ( I'm using Karmic ). I'm not sure if that matters or not. My xinput version is 1.4.2.

I'm curious about this in your Xorg.0.log

```

AUDIT: Fri Dec 18 12:14:42 2009: 5525 X: client 4 rejected from local host ( uid=0 gid=0 pid=5710 )
AUDIT: Fri Dec 18 12:14:49 2009: 5525 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5775 )
AUDIT: Fri Dec 18 12:14:49 2009: 5525 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5776 )
AUDIT: Fri Dec 18 12:14:49 2009: 5525 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5777 )

```
This may be what happens when the mouse fails...

---

### Post by Daddyo-613 on 2009-12-21
It's interesting, I found this link to a similar error message [http://ubuntuforums.org/showthread.php?t=193670](http://ubuntuforums.org/showthread.php?t=193670) the issue there arose with an update from 5.10 to 6.06 and seemed to be solved by reinstalling the nVidia drivers. One of the posts had an excerpt from the Xorg.log file and the [Audit] message folled an error relating to the loading of the nVidia driver.

Here's and excerpt from my Xorg log this morning. BTW my mouse just stopped working...then the keyboard froze. I couldn't bring up a terminal to try the suggested command to stop and restart the mouse and had to do a hard boot.```
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 2.0.99
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Mouse? 1.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: always reports core events
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: Device: "/dev/input/event2"
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Configuring as mouse
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse? 1.00" (type: MOUSE)
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Mon Dec 21 09:24:47 2009: 6367 X: client 4 rejected from local host ( uid=0 gid=0 pid=6382 )
AUDIT: Mon Dec 21 09:24:55 2009: 6367 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6386 )
AUDIT: Mon Dec 21 09:24:55 2009: 6367 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6387 )
AUDIT: Mon Dec 21 09:24:55 2009: 6367 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6388 )
```This is very frustrating...my mouse stopped again. I'm going to post this reply as is and try to stop and restart the mouse from a tty terminal before my keyboard shuts down.

Ok, I'm back. I couldn't open a terminal before my keyboard froze as well. So I had to do a hard boot again...that can't be good. Once the bootup completed and before I even opened the browser, I opened a tty terminal and tried the <xint set-int-prop> command suggested by pbrane. The message I received was that the X session could not be accessed. So I returned to the GUI and opened a terminal and executed the <xinit list> command to get the description of the conected mouse and then used <xinput set-int-prop "Microsoft Microsoft Wireless Optical Mouse? 1.00" "Device Enabled" 32 0> to disable the mouse and  <xinput set-int-prop "Microsoft Microsoft Wireless Optical Mouse? 1.00" "Device Enabled" 32 1> to reinable it. Both commands worked.

I suppose the next step is to wait for the mouse to freeze again and see if I can access a terminal with the keyboard and reinable the mouse during a freeze. If that works it will be an improvement but it will not have identified what is causing the problem.

If there is someone out there who can tell me what to look for or what to post from my log files that might help diagnose the problem that would be appreciated.

---

### Post by fragos on 2009-12-21
If your mouse has a wheel, I think the issue may be the wheel emulation and Machintosh mouse function. You shouldn't need them.

---

### Post by Daddyo-613 on 2009-12-21
fragos;

I think you may be right and that's why I titled this thread "How to Change Default Mouse".

So the question is ... how to I go about making that change. Right now dmesg |grep reports:```
stephen@stephen-desktop:~$ dmesg |grep mouse
[    1.938435] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.944740] mice: PS/2 mouse device common for all mice

```

There is no mention of my MS Wireless mouse from the Kernel because the mouse I'm using is detected by HAL and loaded by xinit.

Any suggestions?

---

### Post by fragos on 2009-12-21
The 1st place to look is /etc/X11/xorg.conf. There should be nothing in there about a mouse. If a mouse is mentioned I believe it will override the hal mouse config.

---

### Post by Daddyo-613 on 2009-12-21
fragos;

Thanks for responding. The following is the contents of my xorg.conf file:```
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

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

``` I draw your attention to the comment ```
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
``` My understanding is that since the inclusion of 'hotplugging' a USB mouse is not configured in the xorg.confg file and that essentially any such entries will be ignored. Have I missed something?

---

### Post by fragos on 2009-12-21
It would appear that my thoughts on Macintosh emulation may be wrong. I looked my my xorg log and found similar Macintosh mouse button emulation statements. I can see in this log my Wacom, Cirque USB Glidepad and Logitech Optical mouse being recognized. I have no other ideas other than to repost your message as perhaps Microsoft Wireless Mouse freezes. Asking a question differently may help since there really isn't a default mouse.

---

### Post by Daddyo-613 on 2009-12-21
I've been trying to follow up on comments from pbrane about the error messages that appear in my Xorg.0.log ```
AUDIT: Fri Dec 18 12:14:42 2009: 5525 X: client 4 rejected from local host ( uid=0 gid=0 pid=5710 )
AUDIT: Fri Dec 18 12:14:49 2009: 5525 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5775 )
AUDIT: Fri Dec 18 12:14:49 2009: 5525 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5776 )
AUDIT: Fri Dec 18 12:14:49 2009: 5525 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5777 )
```WIKI [AUDIT] refers to a security audit. The local host is my computer. The pid=number is the process identification number of the process that was rejected.

I opened my System manager to see if I could identify what processes had those pid numbers but of course they have been rejected so they weren't running. I've checked the other logs to see if there were any references to the pid's that failed and those numbers aren't listed.

Does anyone know how I can follow up on this lead?

Here is the output from a terminal of the current processes that running on my system: ```
stephen@stephen-desktop:~$ ps -eo pid,%cpu,vsz,args,wchan
  PID %CPU    VSZ COMMAND                     WCHAN
    1  0.0   3056 /sbin/init                  select
    2  0.0      0 [kthreadd]                  kthreadd
    3  0.0      0 [migration/0]               migration_thread
    4  0.0      0 [ksoftirqd/0]               ksoftirqd
    5  0.0      0 [watchdog/0]                watchdog
    6  0.0      0 [migration/1]               migration_thread
    7  0.0      0 [ksoftirqd/1]               ksoftirqd
    8  0.0      0 [watchdog/1]                watchdog
    9  0.0      0 [events/0]                  worker_thread
   10  0.0      0 [events/1]                  worker_thread
   11  0.0      0 [khelper]                   worker_thread
   51  0.0      0 [kintegrityd/0]             worker_thread
   52  0.0      0 [kintegrityd/1]             worker_thread
   54  0.0      0 [kblockd/0]                 worker_thread
   55  0.0      0 [kblockd/1]                 worker_thread
   57  0.0      0 [kacpid]                    worker_thread
   58  0.0      0 [kacpi_notify]              worker_thread
  183  0.0      0 [cqueue]                    worker_thread
  187  0.0      0 [kseriod]                   serio_thread
  231  0.0      0 [pdflush]                   pdflush
  232  0.0      0 [pdflush]                   pdflush
  233  0.0      0 [kswapd0]                   kswapd
  275  0.0      0 [aio/0]                     worker_thread
  276  0.0      0 [aio/1]                     worker_thread
 1412  0.0      0 [ksuspend_usbd]             worker_thread
 1413  0.0      0 [khubd]                     hub_thread
 1452  0.0      0 [ata/0]                     worker_thread
 1454  0.0      0 [ata/1]                     worker_thread
 1456  0.0      0 [ata_aux]                   worker_thread
 2171  0.0      0 [scsi_eh_0]                 scsi_error_handler
 2172  0.0      0 [scsi_eh_1]                 scsi_error_handler
 2183  0.0      0 [scsi_eh_2]                 scsi_error_handler
 2184  0.0      0 [scsi_eh_3]                 scsi_error_handler
 2219  0.0      0 [scsi_eh_4]                 scsi_error_handler
 2221  0.0      0 [usb-storage]               usb_stor_control_thread
 2258  0.0      0 [scsi_eh_5]                 scsi_error_handler
 2259  0.0      0 [scsi_eh_6]                 scsi_error_handler
 2422  0.0      0 [kjournald]                 kjournald
 2596  0.0   2528 /sbin/udevd --daemon        select
 4529  0.0   1780 /sbin/getty 38400 tty4      read_chan
 4530  0.0   1780 /sbin/getty 38400 tty5      read_chan
 4537  0.0   1780 /sbin/getty 38400 tty2      read_chan
 4538  0.0   1780 /sbin/getty 38400 tty3      read_chan
 4539  0.0   1780 /sbin/getty 38400 tty6      read_chan
 4726  0.0   2308 /usr/sbin/acpid -c /etc/acp poll
 4769  0.0      0 [kondemand/0]               worker_thread
 4771  0.0      0 [kondemand/1]               worker_thread
 4854  0.0   2012 /sbin/syslogd -u syslog     select
 4906  0.0   1940 /bin/dd bs 1 if /proc/kmsg  syslog
 4908  0.0   4128 /sbin/klogd -P /var/run/klo pipe_wait
 4931  0.0   2960 /bin/dbus-daemon --system   poll
 4953  0.0   3016 avahi-daemon: running [step poll
 4954  0.0   2888 avahi-daemon: chroot helper unix_stream_data_wait
 4968  0.0   7712 /usr/bin/vmware-usbarbitrat poll
 5049  0.0   2084 /usr/bin/vmnet-bridge -s 6  poll
 5057  0.0   2672 /usr/bin/vmnet-dhcpd -s 6 - select
 5060  0.0   2064 /usr/bin/vmnet-netifup -s 6 pause
 5062  0.0   2672 /usr/bin/vmnet-dhcpd -s 6 - select
 5065  0.0   2612 /usr/bin/vmnet-natd -s 6 -m poll
 5068  0.0   2064 /usr/bin/vmnet-netifup -s 6 pause
 5119  0.0   6432 /usr/sbin/cupsd             ep_poll
 5279  0.0   9220 /usr/sbin/winbindd          select
 5301  0.0   9220 /usr/sbin/winbindd          select
 5302  0.0   6448 /usr/sbin/hald              poll
 5305  0.0  17480 /usr/sbin/console-kit-daemo poll
 5306  0.0   3364 hald-runner                 poll
 5388  0.0   3436 hald-addon-input: Listening poll
 5393  0.0   3448 /usr/lib/hal/hald-addon-cpu poll
 5394  0.0   2296 hald-addon-acpi: listening  unix_stream_data_wait
 5397  0.0   3440 hald-addon-storage: polling poll
 5412  0.0   3440 hald-addon-storage: no poll poll
 5444  0.0   3484 /usr/sbin/bluetoothd        poll
 5453  0.0      0 [btaddconn]                 worker_thread
 5454  0.0      0 [btdelconn]                 worker_thread
 5467  0.0      0 [krfcommd]                  rfcomm_run
 5508  0.0  14572 /usr/sbin/NetworkManager    poll
 5517  0.0   4248 /sbin/wpa_supplicant -u -f  select
 5521  0.0   6712 /usr/sbin/nm-system-setting poll
 5546  0.0  14260 /usr/sbin/gdm               poll
 5548  0.0  14804 /usr/sbin/gdm               select
 5553  2.3  48520 /usr/X11R6/bin/X :0 -br -au select
 5569  0.0   4336 /usr/bin/system-tools-backe poll
 5603  0.0   2068 /usr/sbin/atd               hrtimer_nanosleep
 5631  0.0   3412 /usr/sbin/cron              hrtimer_nanosleep
 5710  0.0   1780 /sbin/getty 38400 tty1      read_chan
 5729  0.0   2248 /sbin/dhclient -d -sf /usr/ select
 5807  0.0   6456 /usr/bin/gnome-keyring-daem poll
 5818  0.0  25332 x-session-manager           poll
 5902  0.0   3124 /usr/bin/dbus-launch --exit select
 5903  0.0   3168 //bin/dbus-daemon --fork -- poll
 5906  0.0  28968 /usr/bin/pulseaudio -D --lo poll
 5909  0.0   7532 /usr/lib/pulseaudio/pulse/g poll
 5911  0.0   8020 /usr/lib/libgconf2-4/gconfd poll
 5918  0.0  18140 /usr/bin/seahorse-agent --e poll
 5923  0.0  44596 /usr/lib/gnome-settings-dae poll
 5932  0.0   5560 /usr/lib/gvfs/gvfsd         poll
 5933  0.1  52764 gnome-panel                 poll
 5934  0.0  69148 nautilus --no-desktop --bro poll
 5936  0.0  41748 /usr/lib/bonobo-activation/ poll
 5937  0.0  31256 python /usr/share/screenlet poll
 5939  0.0  30916 trackerd                    poll
 5943  0.0  30848 /usr/bin/python /usr/bin/fu poll
 5944  0.0  31872 /usr/bin/python /usr/bin/bl poll
 5945  0.0  39488 python -u /home/stephen/.sc poll
 5947  0.0  65692 /usr/lib/evolution/2.24/evo poll
 5952  0.0  29196 /usr/lib/gvfs//gvfs-fuse-da futex_wait
 5957  0.0  26152 python /usr/share/system-co poll
 5965  0.1 109304 cairo-dock -o               poll
 5966  0.0  29436 update-notifier             poll
 5967  0.0  19704 /usr/bin/metacity --replace poll
 5968  0.0  16180 tracker-applet              poll
 5969  0.0  28180 nm-applet --sm-disable      poll
 5983  0.0  24652 gnome-power-manager         poll
 6049  0.0  14276 /usr/lib/gvfs/gvfs-hal-volu poll
 6072  0.0   5700 /usr/lib/gvfs/gvfs-gphoto2- poll
 6075  0.0   5556 /usr/lib/gvfs/gvfsd-burn -- poll
 6077  0.0  21772 gnome-screensaver           poll
 6080  0.0  69708 /usr/lib/evolution/evolutio poll
 6095  0.0  32804 /usr/lib/evolution/2.24/evo poll
 6147  0.1  29932 /usr/lib/gnome-panel/sensor poll
 6153  0.0  22196 /usr/lib/gvfs/gvfsd-trash - poll
 6155  0.0  41972 /usr/lib/gnome-applets/tras poll
 6163  0.0  11388 /usr/bin/obex-data-server - poll
 6169  0.0      0 [kjournald]                 kjournald
 6184  0.0  30048 /usr/lib/fast-user-switch-a poll
 6186  0.0  49744 /usr/lib/gnome-applets/mixe poll
 6271  2.4 195296 /usr/lib/firefox-3.0.16/fir poll
 6363  1.2  43100 gnome-system-log            poll
 6365  7.6  43892 gnome-system-monitor        poll
 6378  3.0  94836 gnome-terminal              poll
 6381  0.0   2912 gnome-pty-helper            unix_stream_data_wait
 6382  1.0   5812 bash                        wait
 6399  0.0   2516 ps -eo pid,%cpu,vsz,args,wc -

```Does any of this give a clue as to what may be making my mouse crash?

---

### Post by Daddyo-613 on 2009-12-21
Well sports fans...I finally gave up. Thanks to fagos and pbrane for trying to help.

I've reformatted my hard drive and I'm starting with a fresh installation of Karmic Koala.

My mouse appears to be working...but I'll have to give it some time. I'll try to return to this post to let folks know if the problems resurfaced...in the mean time reconstructing the set up of my system.

BTW I did back up my hard drive and virtual machines onto an external hard drive before I took the plunge.

TTFN

---

