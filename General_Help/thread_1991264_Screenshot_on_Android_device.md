---
title: "Screenshot on Android device"
date: 2012-05-30
forum: General Help
---

### Post by ELMIT on 2012-05-30
I have installed Android SDK into the directory ~/Android/android-sdk-linux

I added into .profile the line:

PATH="$HOME/Android/android-sdk-linux/tools:$HOME/Android/android-sdk-linux/platform-tools:$PATH"

I added a file /etc/udev/rules.d/90-android.rules with the content:
BUS=="usb", SYSFS{idVendor}=="0bb4", OWNER="MACHINEUSERNAME", GROUP="USERGROUP"

And finally I restarted udev:
gksudo service udev restart


I set my HTC phone: Settings -> System -> Develop option -> USB debugging

I plug in the USB cable to the phone and Linux box
A screen pops up if I want to use only charging or access to the USB storage. 

I start ddms and get a Window "Dalvik Debug Monitor" with a phone Name
???????????     |??     |   |  | unknown

If I use USB cable only nothing happens, if I use access USB storage, a window pops up how to use the storage.


What am I missing? How to get the phone connected? How to get the screenshot????

---

### Post by ELMIT on 2012-05-30
In the original description ([https://help.ubuntu.com/community/AndroidScreenshots](https://help.ubuntu.com/community/AndroidScreenshots)) the sentence:

"on some recent UDEVs this has changed to"  let me assume that 12.04 must be a more recent way ... and so I used the line:

BUS=="usb", SYSFS{idVendor}=="0bb4", OWNER="MACHINEUSERNAME", GROUP="USERGROUP"

Changing it to the other line:
SUBSYSTEM=="usb", ATTRS{idVendor}=="0bb4", MODE="0666"

made it work!

---

