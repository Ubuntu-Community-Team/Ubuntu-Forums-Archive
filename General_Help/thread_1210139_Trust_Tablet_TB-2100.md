---
title: "Trust Tablet TB-2100"
date: 2009-07-11
forum: General Help
---

### Post by GCoffee on 2009-07-11
Hi guys,

Just wondering if anyone knows if there are linux drivers for this tablet? 

I've had it a while now and still have the original setup CD.

Thanks,
GCoffee.

---

### Post by Favux on 2009-07-18
Hi GCoffee,

First you have to figure out if it's been rebranded and if so who the original manufacturer is.

Post #11 by practic has several ways to do this:  [http://ubuntuforums.org/showthread.php?t=1151464&page=2](http://ubuntuforums.org/showthread.php?t=1151464&page=2)

Hope this helps.  Good luck!

---

### Post by mooortin on 2010-02-25
HI,

Ok i just take the post for my problem :D 
I get the same tablet Trust TB-2100, also called APT-6000U on linux. Name comes from the manufacturer Aiptek, we all agreed on this! 
AND IT'S NOT WORKING !

Ok so i've been there :   [http://ubuntuforums.org/showthread.php?t=1151464&page=2](http://ubuntuforums.org/showthread.php?t=1151464&page=2)
i've done all what he said and more. i mean, i've been looking on google, on different forums and here. i've been installing, uninstalling, etc for three days and now i get :

$ ls -la /dev/tablet-event  :cannot do that, the file or folder doesn't exist (terminal)

$ cat /sys/bus/usb/devices/*/product : APT-6000U

$ grep -i name /proc/bus/input/devices : N: Name="Aiptek"

$ lsusb -v :
```
Bus 002 Device 002: ID 08ca:0020 Aiptek International, Inc. APT-6000U Tablet
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x08ca Aiptek International, Inc.
  idProduct          0x0020 APT-6000U Tablet
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              3 
      ** UNRECOGNIZED:  09 21 01 01 00 01 22 86 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               3
cannot read device status, Operation not permitted (1)

``` i gave only the part with my Tablet.

$ lshal | less :
```
udi = '/org/freedesktop/Hal/devices/usb_device_8ca_20_noserial_if0'
  info.linux.driver = 'aiptek'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8ca_20_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8ca_20_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0'  (string)
  usb.max_power = 50  (0x32)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 32  (0x20)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Aiptek International, Inc.'  (string)
  usb.vendor_id = 2250  (0x8ca)  (int)
  usb.version = 1.0 (1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_8ca_20_noserial_if0_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keys', 'input.mouse', 'input.tablet', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_8ca_20_noserial_if0'  (string)
  info.product = 'Aiptek'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_8ca_20_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_8ca_20_noserial_if0'  (string)
  input.product = 'Aiptek'  (string)
  input.x11_driver = 'wizardpen'  (string)
  input.x11_options.BottomX = '18800'  (string)
  input.x11_options.BottomY = '12000'  (string)
  input.x11_options.MaxX = '18800'  (string)
  input.x11_options.MaxY = '12000'  (string)
  input.x11_options.SendCoreEvents = 'true'  (string)
  input.x11_options.TopX = '200'  (string)
  input.x11_options.TopY = '200'  (string)
  input.x11_options.bottomZ = '511'  (string)
  input.x11_options.maxZ = '511'  (string)
  input.x11_options.topZ = '5'  (string)
  input.xkb.layout = 'fr'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  input.xkb.variant = 'oss'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0/input/input6/event6'  (string)
```i get also 4 .fdi files :
10-aiptek.fdi (etc/hal/fdi/policy) i wrote "Aiptek" for product.info
10-linuxaiptek.fdi (usr/share/hal/fdi/policy) "Aiptek"
99-x11-wizardpen.fdi (etc/hal/fdi/policy) "APT-6000U"     
10-linuxwacom.fdi (usr/share/hal/fdi/policy/20thirdparty) "Wacom"

For the Xorg.0.log
i get no errors and about the Aiptek tablet i get:

```
(II) config/hal: Adding input device Aiptek
(II) LoadModule: "aiptek"
(II) Loading /usr/lib/xorg/modules/input//aiptek_drv.so
(II) Module aiptek: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.2.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) xf86AiptekInit(): begins
(**) xf86AiptekConfig: device not shared btw Aiptek and Aiptek
(**) Option "SendCoreEvents" "true "
(**) Aiptek: always reports core events
(**) Option "Device" "/dev/input/event6"
(==) HID Device name: "Aiptek"
(==) HID Driver Version: 1.0.0
(==) HID Driver knows it has 1 devices configured
(==) HID Driver is using 24 as the fd
From ioctl() xCapacity=2999
From ioctl() yCapacity=2249
(**) Aiptek device is /dev/input/event6
(**) Aiptek is in absolute mode
(**) Option "USB" "On"
(**) Aiptek: reading USB link
(**) Option "ZMax" "1024"
(**) Aiptek: ZMax/MaxZ = 1024
(**) Option "ZMin" "0"
(**) Aiptek: ZMin/MinZ = 0
(**) Option "BaudRate" "9600"
(**) Aiptek: BaudRate 9600
(**) Aiptek: xf86AiptekInit() finished
(II) XINPUT: Adding extended input device "Aiptek" (type: Stylus)
(**) xTop invalid; adjusted to 0
(**) yTop invalid; adjusted to 0
(**) xBottom invalid; adjusted to 2999
(**) yBottom invalid; adjusted to 2249
(**) ScreenNo invalid; adjusted to 0
(==) HID Device name: "Aiptek"
(==) HID Driver Version: 1.0.0
(==) HID Driver knows it has 1 devices configured
(==) HID Driver is using 24 as the fd
From ioctl() xCapacity=2999
From ioctl() yCapacity=2249
Able to open aiptek device

```I'm on Ubuntu Karmic 64 bits (9.10), I'm desperate, i'm even turning insane.... :$
please my Tablet isn't working, i do need your help
Hopefully i've been clear enough for ya to understand and maybe see where i'm wrong, cause i am but donno where ??
THX

---

### Post by Favux on 2010-02-25
Hi mooortin,

Not for sure I know what's going on but maybe if we work on it together?

First it's definitely an Aiptek:
```
  idVendor           0x08ca Aiptek International, Inc.
  idProduct          0x0020 APT-6000U Tablet

```
```
  usb.vendor = 'Aiptek International, Inc.'  (string)
  usb.vendor_id = 2250  (0x8ca)  (int)

```
I also see in lshal that:
```
input.x11_driver = 'wizardpen'  (string)
```
the WizardPen driver is configuring your tablet.  You may be able to use it, but may want to try the Aiptek driver first.  So is the xserver-xorg-input-aiptek driver installed?  Check Synaptic Package Manager and search Aiptek.

The next problem is that there seem to be multiple .fdi's:
```
10-aiptek.fdi (etc/hal/fdi/policy) i wrote "Aiptek" for product.info
10-linuxaiptek.fdi (usr/share/hal/fdi/policy) "Aiptek"
99-x11-wizardpen.fdi (etc/hal/fdi/policy) "APT-6000U"
10-linuxwacom.fdi (usr/share/hal/fdi/policy/20thirdparty) "Wacom"
```
You want only one .fdi for the tablet.  If you changed the match lines to include "Aiptek" in the wacom and wizardpen .fdi's remove that so they no longer apply.

On the two Aiptek.fdi's was one already installed?  And did you install the one in "etc/hal/fdi/policy"?  We need to look at those two.

And here is a sample aiptek.fdi we came up with:  [http://ubuntuforums.org/showpost.php?p=7604483&postcount=50](http://ubuntuforums.org/showpost.php?p=7604483&postcount=50)  May not be quite right for you, your zMax might be 1023 for example.

I'm not sure what's happening in Xorg.0.log.  It seems good.  Although I expect somewhere in there the WizardPen driver is saying errors.

---

### Post by mooortin on 2010-02-26
hi Favux,
happy to work on this with you.

ok so i get Aiptek driver installed and it's the 1:1.2.0-2 version. (from synaptic)

what sould i removed? the file .fdi for Wizardpen and Wacom ? or simply the Aiptek lines that i added. (in fact only in wizardpen i did it)
-> so i'll delete the fdi's and then restart my computer.

back in five....

---

### Post by mooortin on 2010-02-26
ok i've changed the 10-aiptek.fdi file before i restarted with what you gave me.
the tablet doesn't work just like before but that time i get an error (good! we could know what it is)
Xorg.0.log:
```
(II) config/hal: Adding input device stylus
(II) LoadModule: "aiptek"
(II) Loading /usr/lib/xorg/modules/input//aiptek_drv.so
(II) Module aiptek: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.2.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) xf86AiptekInit(): begins
(**) xf86AiptekConfig: device not shared btw stylus and stylus
(**) Option "SendCoreEvents" "true "
(**) stylus: always reports core events
(**) Option "Device" "/dev/input/event6"
(==) HID Device name: "Aiptek"
(==) HID Driver Version: 1.0.0
(==) HID Driver knows it has 1 devices configured
(==) HID Driver is using 24 as the fd
From ioctl() xCapacity=2999
From ioctl() yCapacity=2249
(**) stylus device is /dev/input/event6
(EE) stylus: invalid Mode ('normal', 'soft' or 'hard').
(**) stylus is in absolute mode
(**) Option "USB" "on"
(**) stylus: reading USB link
(**) Option "ZThreshold" "5"
(**) stylus: ZThreshold/ThresholdZ = 5
(**) Option "ZMax" "1024"
(**) stylus: ZMax/MaxZ = 1024
(**) Option "ZMin" "0"
(**) stylus: ZMin/MinZ = 0
(**) Option "BaudRate" "9600"
(**) stylus: BaudRate 9600
(**) stylus: xf86AiptekInit() finished
(II) XINPUT: Adding extended input device "stylus" (type: Stylus)
(**) xTop invalid; adjusted to 0
(**) yTop invalid; adjusted to 0
(**) xBottom invalid; adjusted to 2999
(**) yBottom invalid; adjusted to 2249
(**) ScreenNo invalid; adjusted to 0
(==) HID Device name: "Aiptek"
(==) HID Driver Version: 1.0.0
(==) HID Driver knows it has 1 devices configured
(==) HID Driver is using 24 as the fd
From ioctl() xCapacity=2999
From ioctl() yCapacity=2249
Able to open aiptek device
```so Wacom and Wizardpen .fdi files are not anymore in the places where they belong, and they won't interfere.
One more point, Why do i get this at the first line: "config/hal: Adding input device stylus" and lower down i get "XINPUT: Adding extended input device "stylus" (type: Stylus)" is that two different things? two different drivers? cause they don't really get the same version....

How do i fix the error? "stylus" is a bit everywhere in the 10-Aiptek Fdi file...
As you can see i'm lost, but maybe you'll be less than me ;)
Thx, talk to you soon.

---

### Post by mooortin on 2010-02-26
It's getting very weird !!!
Let me tell you why : i got two different fdi flies about my tablet. 
the 10-linuxaiptek and 10-aiptek. with different scripts inside (if we can call that a script for me it's all Chinese in english ) so i've decide to make them the same with different name but same script inside.
I've restart my computer, and read the Xorg.0.log :
```
 (II) config/hal: Adding input device stylus
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Option "SendCoreEvents" "true "
(**) stylus: always reports core events
(**) stylus: Device: "/dev/input/event6"
(II) stylus: Found 3 mouse buttons
(II) stylus: Found x and y relative axes
(II) stylus: Found scroll wheel(s)
(II) stylus: Found x and y absolute axes
(II) stylus: Found absolute touchpad
(II) stylus: Found keys
(II) stylus: Configuring as touchpad
(II) stylus: Configuring as keyboard
(**) stylus: YAxisMapping: buttons 4 and 5
(**) stylus: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "stylus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fr"
(**) Option "xkb_variant" "oss"
(WW) stylus: touchpads and touchscreens ignore relative axes.
(**) stylus: (accel) keeping acceleration scheme 1
(**) stylus: (accel) filter chain progression: 2.00
(**) stylus: (accel) filter stage 0: 20.00 ms
(**) stylus: (accel) set acceleration profile 0
(II) stylus: initialized for absolute axes. 
```and what is my suprise when i read this, i don't get aiptek any more i get a stylus tablet !! why not?!? 
So i tested tablet and it worked, it needs 1 or 2 sec to get the control of the scroll. the only problem is the screen is too small,i mean, i'm not using all my tablet.
secondly the buttons don't work (on the pen), if we are talking about those tiny ones. 
I get a mouse with the tablet so i tried. the mouse doesn't control the scroll but just like magic it controls the left and the right click with the buttons.
So i finally tried the mouse plus the pen. but when i pressed the mouse's button that made the scroll moved a bit up and when i released the scroll went back to the initial position. WEIRD ISN'T IT ? :D

we're getting close to it i feel it !!!

---

### Post by Favux on 2010-02-26
Hi mooortin,

In your last post it seems it is the evdev driver running things:
```
II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"

```

You didn't answer my question about the two Aiptek .fdi's.  You only want one, which is why I asked.  I wanted to keep the one the Aiptek driver from Synaptic installed, if it did install one.  And work at that location.  The confusion with two styli is probably because you were running two aiptek.fdi's.

So you can remove the Aiptek driver through Synaptic and see which aiptek.fdi disappears.  That'll tell us the location the driver wants the .fdi.  And then you can remove the other one.  Then just reinstall the Aiptek driver through Synaptic and it should reinstall the .fdi (if it has a .fdi).  So be sure to make back up copies of both of your Aiptek .fdi's before you do anything.

I didn't want you to delete the WizardPen or Wacom .fdi's just to remove the match line you added in WizardPen, or at least your Aiptek model name you added to the match line so it doesn't match to it.  But no harm done.

So once that's cleaned up it should be working.  We may have to fine tune the .fdi a little which is why I linked you to the sample.

---

### Post by mooortin on 2010-02-27
Hi Favux,
No fdi file disappeared, i did the complet removing solution on synaptic to 
be sure that config files will be deleted. but i still get the two fdi files....
i remenber one thing: i've been there [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) 
and it's from there that i got the 10-linuxaiptek.fdi file if it could help.
But i still don't know wich to supress, i think i'll suppress aiptek.fdi file. because they tell me to create the other fdi file for the driver from synaptic. makes sense !!

be back in a while... :D

---

### Post by mooortin on 2010-02-27
ok one more question :
> I didn't want you to delete the WizardPen or Wacom .fdi's just to remove the match line you added in WizardPen, or at least your Aiptek model name you added to the match line so it doesn't match to it. But no harm done.if i understood what you said, : 
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
<device>
<!-- This MUST match with the name of your tablet -->
<match key="info.product" contains="[COLOR=Red]Apt-6000U[/COLOR]">
<merge key="input.x11_driver" type="string">wizardpen</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
<merge key="input.x11_options.TopX" type="string">200</merge>
<merge key="input.x11_options.TopY" type="string">200</merge>
<merge key="input.x11_options.BottomX" type="string">18800</merge>
<merge key="input.x11_options.BottomY" type="string">12000</merge>
<merge key="input.x11_options.MaxX" type="string">18800</merge>
<merge key="input.x11_options.MaxY" type="string">12000</merge>
<merge key="input.x11_options.topZ" type="string">5</merge>
<merge key="input.x11_options.bottomZ" type="string">511</merge>
<merge key="input.x11_options.maxZ" type="string">511</merge>
</match>
</device>
</deviceinfo>
```Remove only [COLOR=Red]Apt-6000U[/COLOR] and leave "" ? ok so if i do that i can't control my keyboard anymore when i arrived on the desktop... don't know why. i don't really understand when you say "the match line..."

Ok now, i get only the 10-linuxaiptek.fdi with that inside: (in red what i've modified)
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

    <!-- [COLOR=Red]Aiptek:  Trust Tablet Wireless: TB-2100[/COLOR] -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="[COLOR=Red]Aiptek[/COLOR]">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.USB" type="string">on</merge>
      <merge key="input.x11_options.Mode" type="string">normal</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.zMin" type="string">0</merge>
      <merge key="input.x11_options.zMax" type="string">511</merge>
      <merge key="input.x11_options.ZThreshold" type="string">5</merge>
      <merge key="input.x11_options.Pressure" type="string">linear</merge>
      <merge key="input.x11_options.KeepShape" type="string">On</merge>
    </match>
  </device>
</deviceinfo>
```And i can control the CURSOR (and not the scroll like i said before, Rahh !bloody frenchie :D ) only if i touch the tablet, before when i was trying with many different drivers one day i controlled the cursor without touching the tablet :$ 

hopefully that will help. i feel useless :(

---

### Post by mooortin on 2010-03-03
a small Up !
i do need your help, i need to work with that tablet... :(

---

### Post by KIAaze on 2010-03-04
Quick google results:
[http://ubuntuforums.org/showthread.php?t=525501](http://ubuntuforums.org/showthread.php?t=525501)
[http://aiptektablet.sourceforge.net/](http://aiptektablet.sourceforge.net/)

More help later eventually. ;)

---

### Post by KIAaze on 2010-03-04
Did any of this work?:
[https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)
[http://blog.mymediasystem.net/uncategorized/apt-6000u/](http://blog.mymediasystem.net/uncategorized/apt-6000u/)

I don't have any tablet, so I'm not sure I can help much more. :/

---

### Post by mooortin on 2010-03-06
ok i give up....

i've been trying so many different driver and none is working....

IF someone wants to help me, i'll enjoy it.
i think i need to start everything from the beginning.
My tablet is Aiptek APT-6000U, and I don't know which driver i have to use. I heard so many different stories, sometime the perfect driver is Wizarpen, sometimes it's simply the aiptek or it could even be the wacom!!! Bloody Hell, where am i supposed to go ???
i've tried every single one of them, but didn't work.

I missed something for sure but don't know where? So if someone gets enough patience to help me i'll appreciate it.

FAVUX you've been a good help, but where did you go ??? i'm alone now :?

---

