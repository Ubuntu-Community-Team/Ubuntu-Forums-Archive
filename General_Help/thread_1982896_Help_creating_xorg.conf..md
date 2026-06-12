---
title: "Help creating xorg.conf."
date: 2012-05-19
forum: General Help
---

### Post by youngie on 2012-05-19
Hi I'm hoping to get some help. I've been having some problems with my mouse scroll wheel going back and forward in Firefox and showing the right click menu in other places, I opened a thread in hardware section but I think I know what the problem is. When I look at "xorg.0.log" it is saying that my mouse has 10 buttons but it is a standard 2 button mouse so it should be 5. I believe it can be fixed by changing "ZAxisMapping" in "xorg.conf" but that file doesn't exist so I need to create one. I've tried, ```
sudo Xorg -configure
```
but it gives a fatal error, something about monitor being used or something. Any help would be much appreciated. Thank you.

---

### Post by steeldriver on 2012-05-19
iirc you can't run that command while there's already a running X server (it needs to start X to probe the config - and it can't if there's already an instance running)

you can either boot into the recovery console or login to one of the virtual terminals (VTs) on Ctrl-Alt-F1 thru Ctrl-Alt-F6 and then do[B][FONT=Ubuntu]
[/FONT][/B]```
sudo service lightdm stop #(if using ubuntu 11.10+)

```or

```
sudo service gdm stop #(if using an older version of ubuntu)
```then after you're done running the config, you can restart the desktop with

```
sudo service lightdm start #(if using ubuntu 11.10+)

```or

```
sudo service gdm start #(if using an older version of ubuntu)
```

---

### Post by CatKiller on 2012-05-19
You can just create one with your favourite text editor. AIUI, anything that you don't put in there will use the newer automatic methods to fill in the blanks. Otherwise, man xorg.conf will tell you which bit goes in which section, and it will be mostly things like Configured Monitor. There are samples on the Internet of what a vanilla xorg.conf can look like. If it all goes pear-shaped you can rename the file you created to something else from one of the TTYs (Ctrl-Alt-F1) and you'll be back where you are.

As an alternative, you could see how to amend the rules for the automatic mouse stuff without touching xorg.conf. I know it's possible, although I can't remember how; I think it's an XML file somewhere that you need to edit.

---

### Post by youngie on 2012-05-21
Ok so I logged into tty stopped lightdm and ran the ```
sudo Xorg -configure
``` but it stops with the error "Number of created screens does not match number of detected devices" I have one monitor! This is somewhat starting to p**s me off, why is it detecting my mouse as having 10 buttons? It did not do this in Oneiric with no xorg.conf. Does anybody know what I need to put if I create one with gedit? I haven't a clue. Thanks for the help.
Edit: Can anyone tell me if this is correct?
```
Section "InputDevice"
 Identifier "Mouse0"
 Driver "mouse"
 Option "Protocol"    "auto"
 Option "Device"     "/dev/input/mice"
 Option "Buttons"     "5"
 Option "ZAxisMapping"  "4 5"
 Option "CorePointer"
 Option "SendCoreEvents" "true"
EndSection
```

---

### Post by forrestcupp on 2012-05-21
It might be easier to go through the automated setup with this command
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by steeldriver on 2012-05-21
there's a good chance it created an xorg.conf.new file in spite of the error message - have a look in that and see if you can pull out the relevant "Input Device" section and mod that

---

### Post by youngie on 2012-05-25
Thanks it did create one in home, this is my xorg.conf located in /etc/X11/ 
```
Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
        Option      "Buttons"     "5"
    Option        "ZAxisMapping" "4 5"
EndSection
```But it hasn't changed anything. This is part of my Xorg.0.log maybe someone can make sense and hopefully be able to help. I have a Microsoft wireless keyboard and mouse that run off the same usb but the mouse doesn't work so I'm using a seperate wired mouse. Thanks all for the help.
```
config/udev: Adding input device USB Optical Mouse USB Optical Mouse (/dev/input/event4)
[    40.182] (**) USB Optical Mouse USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    40.182] (II) Using input driver 'evdev' for 'USB Optical Mouse USB Optical Mouse'
[    40.182] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.182] (**) USB Optical Mouse USB Optical Mouse: always reports core events
[    40.182] (**) evdev: USB Optical Mouse USB Optical Mouse: Device: "/dev/input/event4"
[    40.182] (--) evdev: USB Optical Mouse USB Optical Mouse: Vendor 0x9da Product 0x6
[    40.182] (--) evdev: USB Optical Mouse USB Optical Mouse: Found 10 mouse buttons
[    40.182] (--) evdev: USB Optical Mouse USB Optical Mouse: Found scroll wheel(s)
[    40.182] (--) evdev: USB Optical Mouse USB Optical Mouse: Found relative axes
[    40.182] (--) evdev: USB Optical Mouse USB Optical Mouse: Found x and y relative axes
[    40.183] (II) evdev: USB Optical Mouse USB Optical Mouse: Configuring as mouse
[    40.183] (II) evdev: USB Optical Mouse USB Optical Mouse: Adding scrollwheel support
[    40.183] (**) evdev: USB Optical Mouse USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    40.183] (**) evdev: USB Optical Mouse USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    40.183] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4/event4"
[    40.183] (II) XINPUT: Adding extended input device "USB Optical Mouse USB Optical Mouse" (type: MOUSE, id 8)
[    40.183] (II) evdev: USB Optical Mouse USB Optical Mouse: initialized for relative axes.
[    40.183] (**) USB Optical Mouse USB Optical Mouse: (accel) keeping acceleration scheme 1
[    40.183] (**) USB Optical Mouse USB Optical Mouse: (accel) acceleration profile 0
[    40.183] (**) USB Optical Mouse USB Optical Mouse: (accel) acceleration factor: 2.000
[    40.183] (**) USB Optical Mouse USB Optical Mouse: (accel) acceleration threshold: 4
[    40.184] (II) config/udev: Adding input device USB Optical Mouse USB Optical Mouse (/dev/input/mouse1)
[    40.184] (II) No input driver specified, ignoring this device.
[    40.184] (II) This device may have been added with another device file.
[    40.184] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/event2)
[    40.184] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev keyboard catchall"
[    40.184] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wireless Optical Desktop® 2.10'
[    40.184] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.184] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: always reports core events
[    40.184] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Device: "/dev/input/event2"
[    40.185] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Vendor 0x45e Product 0x9d
[    40.185] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found keys
[    40.185] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as keyboard
[    40.185] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input2/event2"
[    40.185] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop® 2.10" (type: KEYBOARD, id 9)
[    40.185] (**) Option "xkb_rules" "evdev"
[    40.185] (**) Option "xkb_model" "pc105"
[    40.185] (**) Option "xkb_layout" "gb"
[    40.185] (**) Option "xkb_variant" "extd"
[    40.186] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/event3)
[    40.186] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev pointer catchall"
[    40.186] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev keyboard catchall"
[    40.186] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wireless Optical Desktop® 2.10'
[    40.186] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.186] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: always reports core events
[    40.186] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Device: "/dev/input/event3"
[    40.186] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Vendor 0x45e Product 0x9d
[    40.186] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found 9 mouse buttons
[    40.186] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found scroll wheel(s)
[    40.186] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found relative axes
[    40.186] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found x and y relative axes
[    40.186] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found absolute axes
[    40.186] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found absolute multitouch axes
[    40.186] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found x and y absolute axes
[    40.186] (--) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Found keys
[    40.186] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as mouse
[    40.186] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Configuring as keyboard
[    40.186] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: Adding scrollwheel support
[    40.186] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: YAxisMapping: buttons 4 and 5
[    40.186] (**) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    40.187] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input3/event3"
[    40.187] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop® 2.10" (type: KEYBOARD, id 10)
[    40.187] (**) Option "xkb_rules" "evdev"
[    40.187] (**) Option "xkb_model" "pc105"
[    40.187] (**) Option "xkb_layout" "gb"
[    40.187] (**) Option "xkb_variant" "extd"
[    40.187] (II) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: initialized for relative axes.
[    40.187] (WW) evdev: Microsoft Microsoft Wireless Optical Desktop® 2.10: ignoring absolute axes.
[    40.187] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) keeping acceleration scheme 1
[    40.187] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration profile 0
[    40.187] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration factor: 2.000
[    40.187] (**) Microsoft Microsoft Wireless Optical Desktop® 2.10: (accel) acceleration threshold: 4
[    40.188] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/js0)
[    40.188] (II) No input driver specified, ignoring this device.
[    40.188] (II) This device may have been added with another device file.
[    40.188] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/mouse0)
[    40.188] (II) No input driver specified, ignoring this device.
[    40.188] (II) This device may have been added with another device file.
```

---

### Post by youngie on 2012-05-28
Bump.

---

### Post by CatKiller on 2012-05-28
The new way of handling removable devices that I alluded to in my earlier post is through [udev]("http://www.reactivated.net/writing_udev_rules.html"). It's probably a fairly straightforward task to amend the existing rule used for your mouse so that it assigns the correct number of buttons.

Also, the scroll wheel will take you back or forward in Firefox if you're holding shift at the same time. It's possible that your mousewheel.withnokey.action value has been changed by something. You can check it by going to about:config in Firefox and finding that key. The value should be 0 for the normal behaviour. If the value is 2 then it will go backwards and forwards through your history.

---

### Post by youngie on 2012-05-31
I did check about:config and it was set to 0. The thing is it's showing the right click menu randomly when I'm scrolling through document viewer for instance. Man, I thought Ubuntu was supposed to be easy to use! So maybe I need to sort out xorg.conf or change evdev files in xorg.conf.d or create udev rules just to stop my standard mouse from being detected as having 10 buttons! Some ease of use is that. I appreciate the help you guys have given, is there any chance some knowledgeable person can explain exactly what I need to do? I apologise if I'm coming across as dumb but coming from windoze this is going straight over my head.

---

### Post by youngie on 2012-06-03
Bumpety Bump! :oops:

---

