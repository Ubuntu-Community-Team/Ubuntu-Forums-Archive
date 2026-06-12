---
title: "[Android] How to adb push to my EVO?"
date: 2011-03-15
forum: General Help
---

### Post by JimBuntu on 2011-03-15
Hello, 

So I have an EVO and am trying to learn how to use adb. What I'm trying to do is push a new bootanimation.zip to it. I have already downloaded the android.sdk and am wondering what to do now?

I have so far been able to, in terminal, do:

"sudo su" and it logs me in as root...

then I try "./adb remount" and it says insufficient permissions for device. 

Then I try "./adb devices" and it says "????????????	no permissions"

During these steps I had my phone hooked up via USB and had USB debugging on and USB storage on. 

Any Takers?

---

### Post by falko on 2011-03-15
Check if Ubuntu has correctly identified the device:

```
adb devices
```

If you see a lot of question marks like this...

```
falko@falko-desktop:~$ adb devices
List of devices attached
????????????        no permissions

falko@falko-desktop:~$
```

... then Ubuntu did not identify your device. In this case create the file /etc/udev/rules.d/51-android.rules...

```
sudo gedit /etc/udev/rules.d/51-android.rules
```

... with the following contents:
```

SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
```

Replace 0bb4 (this is for HTC phones) with the correct vendor ID which you can find here: [http://developer.android.com/guide/developing/device.html#VendorIds](http://developer.android.com/guide/developing/device.html#VendorIds)

Then run:

```
sudo chmod a+r /etc/udev/rules.d/51-android.rules
```

Plug out your phone and plug it back in, and Ubuntu should now recognize it:

```
adb devices
```

```
falko@falko-desktop:~$ adb devices
List of devices attached
SH0ARPL12791        device

falko@falko-desktop:~$
```

(see chapter 8 on [http://www.howtoforge.com/setting-up-an-android-app-build-environment-with-eclipse-android-sdk-phonegap-ubuntu-10.10-p5](http://www.howtoforge.com/setting-up-an-android-app-build-environment-with-eclipse-android-sdk-phonegap-ubuntu-10.10-p5) )

---

### Post by JimBuntu on 2011-03-17
> **falko said:**
> Check if Ubuntu has correctly identified the device:

```
adb devices
```

If you see a lot of question marks like this...

```
falko@falko-desktop:~$ adb devices
List of devices attached
????????????        no permissions

falko@falko-desktop:~$
```

... then Ubuntu did not identify your device. In this case create the file /etc/udev/rules.d/51-android.rules...

```
sudo gedit /etc/udev/rules.d/51-android.rules
```

... with the following contents:
```

SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
```

Replace 0bb4 (this is for HTC phones) with the correct vendor ID which you can find here: [http://developer.android.com/guide/developing/device.html#VendorIds](http://developer.android.com/guide/developing/device.html#VendorIds)

Then run:

```
sudo chmod a+r /etc/udev/rules.d/51-android.rules
```

Plug out your phone and plug it back in, and Ubuntu should now recognize it:

```
adb devices
```

```
falko@falko-desktop:~$ adb devices
List of devices attached
SH0ARPL12791        device

falko@falko-desktop:~$
```

(see chapter 8 on [http://www.howtoforge.com/setting-up-an-android-app-build-environment-with-eclipse-android-sdk-phonegap-ubuntu-10.10-p5](http://www.howtoforge.com/setting-up-an-android-app-build-environment-with-eclipse-android-sdk-phonegap-ubuntu-10.10-p5) )

Wow, thank you... I will do this asap!!! I'll report back and let you know how it went..

Thanks again.

---

### Post by JimBuntu on 2011-03-18
> **falko said:**
> Check if Ubuntu has correctly identified the device:

```
adb devices
```

If you see a lot of question marks like this...

```
falko@falko-desktop:~$ adb devices
List of devices attached
????????????        no permissions

falko@falko-desktop:~$
```

... then Ubuntu did not identify your device. In this case create the file /etc/udev/rules.d/51-android.rules...

```
sudo gedit /etc/udev/rules.d/51-android.rules
```

... with the following contents:
```

SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
```

Replace 0bb4 (this is for HTC phones) with the correct vendor ID which you can find here: [http://developer.android.com/guide/developing/device.html#VendorIds](http://developer.android.com/guide/developing/device.html#VendorIds)

Then run:

```
sudo chmod a+r /etc/udev/rules.d/51-android.rules
```

Plug out your phone and plug it back in, and Ubuntu should now recognize it:

```
adb devices
```

```
falko@falko-desktop:~$ adb devices
List of devices attached
SH0ARPL12791        device

falko@falko-desktop:~$
```

(see chapter 8 on [http://www.howtoforge.com/setting-up-an-android-app-build-environment-with-eclipse-android-sdk-phonegap-ubuntu-10.10-p5](http://www.howtoforge.com/setting-up-an-android-app-build-environment-with-eclipse-android-sdk-phonegap-ubuntu-10.10-p5) )

ok, so i've done everything and now have a device listed!! Perfect... Thank you.

One problem now...

I'm doing, 

./adb push bootanimation.zip system/media

while root...

and I'm getting "failed to copy" "read only file system"

What am I doing wrong?

### Figured it out ###

What I wasn't doing was booting my EVO into recovery and mounting system. Once I did that ./adb push worked perfectly. I now have the Xoom boot animation on my EVO working perfect! Thanks for your help!!

---

