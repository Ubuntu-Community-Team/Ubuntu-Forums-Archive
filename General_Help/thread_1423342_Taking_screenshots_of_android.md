---
title: "Taking screenshots of android"
date: 2010-03-06
forum: General Help
---

### Post by grindboy on 2010-03-06
[B][COLOR="Red"]ALWAYS REBOOT WHEN CHANGING ANYTHING MANUALLY. *headbutts wall to punctuate each word*

Sorry guys :-([/COLOR][/B]

Hi Guys,

I've found [this awesome tutorial ]("https://help.ubuntu.com/community/AndroidScreenshots") for taking screenshots of android using Jaunty but I can't seem to get it to work on Karmic. I've installed the SDK, allowed USB debugging on my phone, created the udev rule and launched the DDMS script which gives me the following:

[IMG]http://dl.dropbox.com/u/896644/Screenshot-Dalvik%20Debug%20Monitor%20.png[/IMG]

As you can see the device shows up but only as ????????? is this a problem with the HTC Hero's version of Android 1.5, the fact that I'm using Karmic not Jaunty or have I made a silly error somewhere.

Hope you can help

Many thanks

Grindboy

[edit] just tried running DDMS in terminal and when I click on the device I get the following:
```
28:54 E/DDMS: device (????????????) request rejected: insufficient permissions for device
java.io.IOException: device (????????????) request rejected: insufficient permissions for device
	at com.android.ddmlib.AdbHelper.setDevice(AdbHelper.java:726)
	at com.android.ddmlib.AdbHelper.executeRemoteCommand(AdbHelper.java:363)
	at com.android.ddmlib.Device.executeShellCommand(Device.java:275)
	at com.android.ddmuilib.SysinfoPanel.loadFromDevice(SysinfoPanel.java:156)
	at com.android.ddmuilib.SysinfoPanel.deviceSelected(SysinfoPanel.java:123)
	at com.android.ddmuilib.SelectionDependentPanel.deviceSelected(SelectionDependentPanel.java:52)
	at com.android.ddms.UIThread.selectionChanged(UIThread.java:1652)
	at com.android.ddmuilib.DevicePanel.notifyListeners(DevicePanel.java:753)
	at com.android.ddmuilib.DevicePanel.notifyListeners(DevicePanel.java:741)
	at com.android.ddmuilib.DevicePanel.access$1100(DevicePanel.java:56)
	at com.android.ddmuilib.DevicePanel$1.widgetSelected(DevicePanel.java:360)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(Unknown Source)
	at org.eclipse.swt.widgets.EventTable.sendEvent(Unknown Source)
	at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Unknown Source)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
	at com.android.ddms.UIThread.runUI(UIThread.java:474)
	at com.android.ddms.Main.main(Main.java:105)


```

Hope that sheds more light

---

### Post by TheCarl on 2010-03-21
To get this woriking on the Nexus One

```
SUBSYSTEMS=="usb", ATTRS{idVendor}=="18d1", ATTRS{idProduct}=="4e12", MODE="0666"
```
I put the code above in
```
/etc/udev/rules.d/51-android.rules
```
and restarted udev
```
reload udev
```

I found the Vendor id and product from here [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)

---

### Post by servilla on 2010-04-03
Placing the device code (below) in the [FONT="Courier New"]/etc/udev/rules.d/51-android.rules[/FONT] file worked for the Motorola Droid on Ubuntu 9.10 (Karmic)

```
SUBSYSTEMS=="usb", ATTRS{idVendor}=="22b8", ATTRS{idProduct}=="41db", MODE="0666"
```

Thanks for the tip!

Mark

---

### Post by jaumedejuan on 2011-03-09
If your device doesn't actually show in the linked list, you can also do a 

```
lsusb

Bus 001 Device 012: ID 19d2:1351 ONDA Communication S.p.A.
``` 

idvendor = 19d2
idproduct = 1351

these codes are for an ZTE Blade/Orange San Francisco.

and thanks for the groundwork to the guys above!

---

### Post by mihai.ile on 2011-04-09
Just for reference, it worked perfectly on Ubuntu 10.10 with an HTC Hero using Cyanogenmod.

---

### Post by walmac_snake on 2011-04-19
just for reference too, it worked with my Samsung Galaxy Ace.

---

### Post by AlienDev on 2011-08-23
thank you so much, this worked perfectly trying to get a tablet to work that the company i work for is developing.

---

