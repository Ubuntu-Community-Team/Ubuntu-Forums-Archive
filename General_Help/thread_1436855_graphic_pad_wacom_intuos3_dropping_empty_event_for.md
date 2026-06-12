---
title: "graphic pad wacom intuos3 dropping empty event for serial"
date: 2010-03-23
forum: General Help
---

### Post by superseed77 on 2010-03-23
Hi all

In now on Karmic on a HP laptop since 8.10
I was configured my wacom intuos via xorg.conf

since my laptop is freezing once a moth i had a look at the Xorg.log and saw a large list of 

```
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
```so I get back to my xorg.conf and I get this
```

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Driver        "wacom"
#    Identifier    "stylus"
#    Option        "Device"    "/dev/input/wacom"
#    Option        "Type"    "stylus"
#    Option        "Mode"          "absolute"            # Position sur la tablette
#    #Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
#    Option         "Tilt"         "on"                  # Inclinaison
#    #Option         "TiltInvert"   "on"                  # Invertion de l'inclinaison
#    Option         "Threshold"     "5"                   # sensibilité à la pression
#
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Driver        "wacom"
#    Identifier    "eraser"
#    Option        "Device"    "/dev/input/wacom"
#    Option        "Type"    "eraser"
#    #Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
#      Option        "Mode"          "absolute"            # Position sur la tablette
#      #Option        "ForceDevice"  "ISDV4"                # Tablet PC ONLY
#      #Option        "HistorySize"  "64"                   # Taille buffer
#      Option         "Tilt"         "on"                  # Inclinaison
#     #Option         "TiltInvert"   "on"                  # Invertion de l'inclinaison
#    Option         "Threshold"     "5"                   # sensibilité à la pression
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Driver        "wacom"
#    Identifier    "cursor"
#    Option        "Device"    "/dev/input/wacom"
#    Option        "Type"    "cursor"
#      #Option        "Mode"          "absolute"            # Position sur la tablette
#      #Option        "ForceDevice"  "ISDV4"                # Tablet PC ONLY
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "pad"
#  Option        "Device"        "/dev/input/wacom"    # Tablette USB
#  Option        "Type"          "pad"
#  Option        "USB"           "on"                  # Tablette USB
#  #Option        "HistorySize"  "64"                  # Taille buffer
#EndSection


Section "Device"
    Identifier    "nVidia Corporation G80 [Quadro FX 1600M]"
    Driver        "nvidia"
    Busid        "PCI:1:0:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
EndSection

```
What a surprise I'm old fashioned !
Hal takes the control !

gathering the forums I found that I should put something in /etc/hal/fdi/policy/
I have on one file : preferences.fdi
```

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
<!--
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
-->
</deviceinfo>

```Question :

Do my problem comes from the fact my wacom tablet don't have an entry in it ?
What do I have to do to fix this problem and take control of how my tablet behave ?

wacomcpl show me an incomplete window with nothing in it ...

Thanx a lot 

here some command output to help to figure the situation
```

lsusb
Bus 002 Device 003: ID 059b:027a Iomega Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 007: ID 056a:00b1 Wacom Co., Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````

xinput --list

"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=10    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
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
"PS/2 Generic Mouse"    id=11    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
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
"SynPS/2 Synaptics TouchPad"    id=12    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
"Wacom Intuos3 6x8 eraser"    id=3    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 40640
        Resolution is 5080
    Axis 1 :
        Min_value is 0
        Max_value is 30480
        Resolution is 5080
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom Intuos3 6x8 cursor"    id=7    [XExtensionKeyboard]
    Type is Wacom Cursor
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 40640
        Resolution is 5080
    Axis 1 :
        Min_value is 0
        Max_value is 30480
        Resolution is 5080
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is -900
        Max_value is 899
        Resolution is 1
    Axis 4 :
        Min_value is -1023
        Max_value is 1023
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom Intuos3 6x8 pad"    id=8    [XExtensionKeyboard]
    Type is Wacom Pad
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 8
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 40640
        Resolution is 5080
    Axis 1 :
        Min_value is 0
        Max_value is 30480
        Resolution is 5080
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is 0
        Max_value is 4096
        Resolution is 1
    Axis 4 :
        Min_value is 0
        Max_value is 4096
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom Intuos3 6x8"    id=9    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 40640
        Resolution is 5080
    Axis 1 :
        Min_value is 0
        Max_value is 30480
        Resolution is 5080
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is -900
        Max_value is 899
        Resolution is 1

``````
xsetwacom list dev
Nope

``````
xsetwacom list param

TopX             - Bounding rect left coordinate in tablet units. 
TopY             - Bounding rect top coordinate in tablet units . 
BottomX          - Bounding rect right coordinate in tablet units. 
BottomY          - Bounding rect bottom coordinate in tablet units. 
Button1          - X11 event to which button 1 should be mapped. 
Button2          - X11 event to which button 2 should be mapped. 
Button3          - X11 event to which button 3 should be mapped. 
Button4          - X11 event to which button 4 should be mapped. 
Button5          - X11 event to which button 5 should be mapped. 
Button6          - X11 event to which button 6 should be mapped. 
Button7          - X11 event to which button 7 should be mapped. 
Button8          - X11 event to which button 8 should be mapped. 
Button9          - X11 event to which button 9 should be mapped. 
Button10         - X11 event to which button 10 should be mapped. 
Button11         - X11 event to which button 11 should be mapped. 
Button12         - X11 event to which button 12 should be mapped. 
Button13         - X11 event to which button 13 should be mapped. 
Button14         - X11 event to which button 14 should be mapped. 
Button15         - X11 event to which button 15 should be mapped. 
Button16         - X11 event to which button 16 should be mapped. 
Button17         - X11 event to which button 17 should be mapped. 
Button18         - X11 event to which button 18 should be mapped. 
Button19         - X11 event to which button 19 should be mapped. 
Button20         - X11 event to which button 20 should be mapped. 
Button21         - X11 event to which button 21 should be mapped. 
Button22         - X11 event to which button 22 should be mapped. 
Button23         - X11 event to which button 23 should be mapped. 
Button24         - X11 event to which button 24 should be mapped. 
Button25         - X11 event to which button 25 should be mapped. 
Button26         - X11 event to which button 26 should be mapped. 
Button27         - X11 event to which button 27 should be mapped. 
Button28         - X11 event to which button 28 should be mapped. 
Button29         - X11 event to which button 29 should be mapped. 
Button30         - X11 event to which button 30 should be mapped. 
Button31         - X11 event to which button 31 should be mapped. 
Button32         - X11 event to which button 32 should be mapped. 
DebugLevel       - Level of debugging trace for individual devices, default is 0 (off). 
CommonDBG        - Level of debugging statements applied to all devices associated with the same tablet. 
           default is 0 (off). 
Suppress         - Number of points trimmed, default is 2. 
RawSample        - Number of raw data used to filter the points, default is 4. 
Screen_No        - Sets/gets screen number the tablet is mapped to, default is -1. 
PressCurve       - Bezier curve for pressure (default is 0 0 100 100). 
TwinView         - Sets the mapping to TwinView xinerama/horizontal/vertical/leftof/aboveof/none. 
           Values = none, vertical, horizontal, leftof, aboveof, xinerama (default is none).
Mode             - Switches cursor movement mode (default is absolute/on). 
TPCButton        - Turns on/off Tablet PC buttons. default is off for regular tablets, on for Tablet PC. 
Touch            - Turns on/off Touch events (default is enable/on). 
Capacity         - Touch sensitivity level (default is 3, -1 for none capacitive tools). 
CursorProx       - Sets cursor distance for proximity-out in distance from the tablet.  
           (default is 10 for Intuos series, 42 for Graphire series). 
Rotate           - Sets the rotation of the tablet. Values = NONE, CW, CCW, HALF (default is NONE). 
           Tablet mappings applied after this command will be based on the new tablet orientation. 
RelWUp           - X11 event to which relative wheel up should be mapped. 
RelWDn           - X11 event to which relative wheel down should be mapped. 
AbsWUp           - X11 event to which absolute wheel up should be mapped. 
AbsWDn           - X11 event to which absolute wheel down should be mapped. 
StripLUp         - X11 event to which left strip up should be mapped. 
StripLDn         - X11 event to which left strip down should be mapped. 
StripRUp         - X11 event to which right strip up should be mapped. 
StripRDn         - X11 event to which right strip down should be mapped. 
TVResolution0    - Sets MetaModes option for TwinView Screen 0. 
TVResolution1    - Sets MetaModes option for TwinView Screen 1. 
RawFilter        - Enables and disables filtering of raw data, default is true/on.
SpeedLevel       - Sets relative cursor movement speed (default is 6). 
ClickForce       - Sets tip/eraser pressure threshold = ClickForce*MaxZ/100 (default is 6)
Threshold        - Sets tip/eraser pressure threshold directly to the pressure (default is 6*MaxZ/100)
Accel            - Sets relative cursor movement acceleration (default is 1)
xyDefault        - Resets the bounding coordinates to default in tablet units. 
mmonitor         - Turns on/off across monitor movement in multi-monitor desktop, default is on 
CoreEvent        - Turns on/off device to send core event. default is decided by X driver and xorg.conf 
STopX0           - Screen 0 left coordinate in pixels. 
STopY0           - Screen 0 top coordinate in pixels. 
SBottomX0        - Screen 0 right coordinate in pixels. 
SBottomY0        - Screen 0 bottom coordinate in pixels. 
STopX1           - Screen 1 left coordinate in pixels. 
STopY1           - Screen 1 top coordinate in pixels. 
SBottomX1        - Screen 1 right coordinate in pixels. 
SBottomY1        - Screen 1 bottom coordinate in pixels. 
STopX2           - Screen 2 left coordinate in pixels. 
STopY2           - Screen 2 top coordinate in pixels. 
SBottomX2        - Screen 2 right coordinate in pixels. 
SBottomY2        - Screen 2 bottom coordinate in pixels. 
STopX3           - Screen 3 left coordinate in pixels. 
STopY3           - Screen 3 top coordinate in pixels. 
SBottomX3        - Screen 3 right coordinate in pixels. 
SBottomY3        - Screen 3 bottom coordinate in pixels. 
STopX4           - Screen 4 left coordinate in pixels. 
STopY4           - Screen 4 top coordinate in pixels. 
SBottomX4        - Screen 4 right coordinate in pixels. 
SBottomY4        - Screen 4 bottom coordinate in pixels. 
STopX5           - Screen 5 left coordinate in pixels. 
STopY5           - Screen 5 top coordinate in pixels. 
SBottomX5        - Screen 5 right coordinate in pixels. 
SBottomY5        - Screen 5 bottom coordinate in pixels. 
STopX6           - Screen 6 left coordinate in pixels. 
STopY6           - Screen 6 top coordinate in pixels. 
SBottomX6        - Screen 6 right coordinate in pixels. 
SBottomY6        - Screen 6 bottom coordinate in pixels. 
STopX7           - Screen 7 left coordinate in pixels. 
STopY7           - Screen 7 top coordinate in pixels. 
SBottomX7        - Screen 7 right coordinate in pixels. 
SBottomY7        - Screen 7 bottom coordinate in pixels. 
ToolID           - Returns the ID of the associated device. 
ToolSerial       - Returns the serial number of the associated device. 
Serial           - Returns/sets the serial number of the chosen device. 
TabletID         - Returns the tablet ID of the associated device. 
GetTabletID      - Returns the tablet ID of the associated device. 
NumScreen        - Returns number of screens configured for the desktop. 
XScaling         - Returns the status of XSCALING is set or not. 

Event description format:
[CORE] [EVENT TYPE] [MODIFIERS] [CODE]
  CORE: Emit core events irrespective of the SendCoreEvents setting
  EVENT TYPE: the type of event to emit:
    KEY: Emit a key event
    BUTTON: Emit a button event
    DBLCLICK: Emit a double-click button event
    MODETOGGLE: Toggle absolute/relative tablet mode
    DISPLAYTOGGLE: Toggle cursor movement among all displays 
        which include individual screens plus the whole desktop 
        for the selected tool if it is not a pad. 
        When the tool is a pad, the function applies to all 
        tools that are asssociated with the tablet
    SCREENTOGGLE: Toggle cursor movement among all screens 
        for the selected tool if it is not a pad. 
        When the tool is a pad, the function applies to all 
        tools that are asssociated with the tablet
  Modifier: use "xsetwacom list mod"
      to see a list of modifiers and specific keys
  CODE: Button number if emitting a button event; 
    or specific keys and any other keys not listed as mod 
Examples:
  xsetwacom set stylus Button1 "button 5"
    (emit mouse button 5 event)
  xsetwacom set stylus Button3 "dblclick 1"
    (emit mouse double left click event)
  xsetwacom set pad Button2 "core key ctrl alt F2"
    (emit ctrl + alt + F2 key event)
  xsetwacom set pad Button3 "core key quotedbl a space test space string quotedbl"
    (emit keystroke "a test string" event)
  xsetwacom set pad Button3 "core key quotedbl a test string quotedbl"
    (emit keystroke "ateststring" event)
  xsetwacom set pad striplup "core key up"
    (emit up arrow key event)
  xsetwacom set pad stripldn "core key down"
    (emit down arrow key event)

```


FOR MORE INFO 
here is my xorg.log when I plus my tablet
```

(II) config/hal: Adding input device Wacom Intuos3 6x8 eraser
(**) Wacom Intuos3 6x8 eraser: always reports core events
(**) Wacom Intuos3 6x8 eraser device is /dev/input/event6
(**) Wacom Intuos3 6x8 eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) Wacom Intuos3 6x8 eraser: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/input/event6"
Wacom Intuos3 6x8 eraser Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom USB Intuos3 tablet speed=9600 (38400) maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080  tilt=enabled
(==) Wacom device "Wacom Intuos3 6x8 eraser" top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
(II) config/hal: Adding input device Wacom Intuos3 6x8 cursor
(**) Wacom Intuos3 6x8 cursor: always reports core events
(**) Wacom Intuos3 6x8 cursor device is /dev/input/event6
(**) Wacom Intuos3 6x8 cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom Intuos3 6x8 cursor: reading USB link
(**) Wacom Intuos3 6x8 cursor: threshold = 61
(**) Wacom Intuos3 6x8 cursor: max x set to 40640 by xorg.conf
(**) Wacom Intuos3 6x8 cursor: max y set to 30480 by xorg.conf
(**) Wacom Intuos3 6x8 cursor: max z = 1023
(**) Option "BaudRate" "9600"
(**) Wacom Intuos3 6x8 cursor: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 cursor" (type: Wacom Cursor)
(==) Wacom device "Wacom Intuos3 6x8 cursor" top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
(II) config/hal: Adding input device Wacom Intuos3 6x8 pad
(**) Wacom Intuos3 6x8 pad: always reports core events
(**) Wacom Intuos3 6x8 pad device is /dev/input/event6
(**) Wacom Intuos3 6x8 pad is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom Intuos3 6x8 pad: reading USB link
(**) Wacom Intuos3 6x8 pad: threshold = 61
(**) Wacom Intuos3 6x8 pad: max x set to 40640 by xorg.conf
(**) Wacom Intuos3 6x8 pad: max y set to 30480 by xorg.conf
(**) Wacom Intuos3 6x8 pad: max z = 1023
(**) Option "BaudRate" "9600"
(**) Wacom Intuos3 6x8 pad: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 pad" (type: Wacom Pad)
(==) Wacom device "Wacom Intuos3 6x8 pad" top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
(II) config/hal: Adding input device Wacom Intuos3 6x8
(**) Wacom Intuos3 6x8: always reports core events
(**) Wacom Intuos3 6x8 device is /dev/input/event6
(**) Wacom Intuos3 6x8 is in absolute mode
(**) WACOM: suppress value is 2
(**) Wacom Intuos3 6x8: reading USB link
(**) Wacom Intuos3 6x8: threshold = 61
(**) Wacom Intuos3 6x8: max x set to 40640 by xorg.conf
(**) Wacom Intuos3 6x8: max y set to 30480 by xorg.conf
(**) Wacom Intuos3 6x8: max z = 1023
(**) Option "BaudRate" "9600"
(**) Wacom Intuos3 6x8: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Intuos3 6x8" (type: Wacom Stylus)
(==) Wacom device "Wacom Intuos3 6x8" top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial -1
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
Wacom Intuos3 6x8 - usbParse: dropping empty event for serial 129740188
...... ad infinitum ...

```

---

