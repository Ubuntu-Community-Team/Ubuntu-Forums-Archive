---
title: "Using android adb with Samsung Moment on Karmic"
date: 2009-12-05
forum: General Help
---

### Post by Peepsalot on 2009-12-05
I'm trying to get android adb tool to recognize my Samsung Moment over usb, but it never sees the device.  From what I've read so far, it looks like you have to edit some udev rules to make this work.  I've read many different pages online, each with slightly different instructions, saying how to make it work for different combinations of linux distro and android device, but none of these are working for me with my Moment on Ubuntu Karmic.

Here are some of the links I've read and tried:

G1 on Ubuntu Dapper/Gutsy/Hardy
[http://developer.android.com/guide/developing/device.html](http://developer.android.com/guide/developing/device.html)
Droid on Karmic:
[http://aphyr.com/journals/show/debugging-the-droid-on-ubuntu-karmic](http://aphyr.com/journals/show/debugging-the-droid-on-ubuntu-karmic)
Magic on Ubuntu Jaunty:
[http://nicolas-raoul.blogspot.com/2009/06/developing-on-android-device-using.html](http://nicolas-raoul.blogspot.com/2009/06/developing-on-android-device-using.html)
Galaxy on debian:
[http://ghantoos.org/2009/08/08/running-debian-on-a-samsung-galaxy-under-android/#root](http://ghantoos.org/2009/08/08/running-debian-on-a-samsung-galaxy-under-android/#root)

I've tried dozens of variations on all of these instructions, but I am unable to get any of them to work.  Each time I always replace whatever idVendor given with the correct value: 04e8 for Samsung devices(verified with lsusb).  Every try I have done, I have the device set in USB debugging mode, I restart udev, unplug/plug in the device, run "adb kill-server", etc.

And every time, "adb devices" just returns an empty list:
```

#./adb devices
List of devices attached

#
```

Any ideas what to do?

---

### Post by thenuge26 on 2009-12-05
I also would like to know, i started setting up my moment so i could root it to get busybox on it (gotta have my grep), and now that i have wiped out my sd card and partitioned it, i cant connect.  I backed up all my files, but  i was ready to go.  I really dont want to boot into my xp boot to do this......

---

### Post by Peepsalot on 2009-12-05
It looks like there is a bug in the linux usb driver: [http://code.google.com/p/android/issues/detail?id=5027](http://code.google.com/p/android/issues/detail?id=5027)

It doesn't look like an official fix has been released yet.

---

### Post by MunksterMan2 on 2010-02-11
A full summary of how to fix this issue:

Download the patch: [http://android.googlecode.com/issues/attachment?aid=1837107545499002241&name=usb_linux.c.patch](http://android.googlecode.com/issues/attachment?aid=1837107545499002241&name=usb_linux.c.patch)

Install necessary software:
sudo apt-get install git-core libncurses5-dev flex

Download the JDK 1.5 (it won't want to compile with 1.6) from [http://java.sun.com/javase/downloads/5u22/jdk](http://java.sun.com/javase/downloads/5u22/jdk) and install it like this:
chmod 755 jdk-1_5_0_22-linux-i586.bin
./jdk-1_5_0_22-linux-i586.bin  (follow the prompts)
sudo update-alternatives --install /usr/bin/javac javac *<path to your new jdk 1.5>*/bin/javac 1
sudo update-alternatives --config javac  (choose the jdk 1.5 version)
javac -version (make sure it says 1.5, otherwise you need to fix something)

Download the android SDK source:
repo init -u git://android.git.kernel.org/platform/manifest.git
repo sync

Apply the downloaded patch:
patch -b system/core/adb/usb_linux.c *<path to your downloaded usb_linux.c.patch>*

Re-compile:
make adb  (make sure there's no errors!)

Overwrite your old adb:
cp out/host/linux-x86/bin/adb *<path to your android sdk>*/tools/adb

Restart adb:
adb kill-server
adb start-server

Connect your moment and see if it shows up:
adb devices

I've noticed occasionally my moment gets in a state where it doesn't know it's connected to the PC and doesnt show the "USB Connected" notification.  Rebooting the phone fixes that.

---

### Post by kris07 on 2010-02-26
Hi, I've been trying to follow these instructions, but when I try:

repo init -u git://android.git.kernel.org/platform/manifest.git

I get: No command 'repo' found, did you mean: etc, etc

How can I fix this?

---

### Post by sad1sm0 on 2010-02-28
> **kris07 said:**
> Hi, I've been trying to follow these instructions, but when I try:

repo init -u git://android.git.kernel.org/platform/manifest.git

I get: No command 'repo' found, did you mean: etc, etc

How can I fix this?

I was just having the same problem that you are.  Repo is a version control system for use specifically with Android, at least from what I understand of it.  [Using Repo and Git]("http://source.android.com/download/using-repo") helped me out. If you've never used curl before, you'll need to install that (use the repos) before you can get it going.

 However, when I go to apply the patch I am getting an error
```

$ patch -b system/core/adb/usb_linux.c ~/Downloads/usb_linux.c.patch

patching file system/core/adb/usb_linux.c
Hunk #1 FAILED at 217.
1 out of 1 hunk FAILED -- saving rejects to file system/core/adb/usb_linux.c.rej

```
I'm stumped on where to go from here.

---

### Post by brian.hillz0r on 2010-04-14
This worked swimmingly. I did, however, have to manually apply the patch. Once I did, I was able to recompile adb and my Moment was listed after running:

./adb devices

Thanks!

---

### Post by spurnout on 2010-05-03
Hey guys, I'm really new to Linux to I'm having a bit of trouble with this part here:

Download the JDK 1.5 (it won't want to compile with 1.6) from [http://java.sun.com/javase/downloads/5u22/jdk](http://java.sun.com/javase/downloads/5u22/jdk)  and install it like this:
chmod 755 jdk-1_5_0_22-linux-i586.bin
./jdk-1_5_0_22-linux-i586.bin  (follow the prompts)
sudo update-alternatives --install /usr/bin/javac javac *<path to  your new jdk 1.5>*/bin/javac 1
sudo update-alternatives --config javac  (choose the jdk 1.5 version)
javac -version (make sure it says 1.5, otherwise you need to fix  something)

I was able to install the java but when I get to the update-alternatives part i'm a bit confused.  When it says path to your new jdk 1.5...I don't know the path!  Did I miss something  somewhere?  Thanks.

---

### Post by sad1sm0 on 2010-05-29
Well I have upgraded to Lucid (HUGE MISTAKE!!!) so my setup might be a little different, but I still haven't managed to get this working.  just did repo sync and got the newest files, however, the [patch]("http://android.googlecode.com/issues/attachment?aid=1837107545499002241&name=usb_linux.c.patch") seems to be gone (Google says Invalid Page)

Also, Can't make adb because it says I'm using the wrong version of java... wtf

```

**$ sudo update-alternatives --config javac**
There are 5 choices for the alternative javac (providing /usr/bin/javac).

  Selection    Path                                     Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/bin/javac     1061      auto mode
* 1            /home/sad1sm0/bin/jdk1.5.0_22/bin/javac   1         manual mode
  2            /usr/bin/ecj                              143       manual mode
  3            /usr/bin/gcj-wrapper-4.3                  43        manual mode
  4            /usr/lib/jvm/java-6-openjdk/bin/javac     1061      manual mode
  5            /usr/lib/jvm/java-6-sun/bin/javac         63        manual mode

**$ javac -version**
javac 1.5.0_22
...
**$ make adb**
============================================
PLATFORM_VERSION_CODENAME=REL
PLATFORM_VERSION=2.1-update1
TARGET_PRODUCT=generic
TARGET_BUILD_VARIANT=eng
TARGET_SIMULATOR=
TARGET_BUILD_TYPE=release
TARGET_ARCH=arm
HOST_ARCH=x86
HOST_OS=linux
HOST_BUILD_TYPE=release
BUILD_ID=ECLAIR
============================================
/bin/bash: bison: command not found
Checking build tools versions...
************************************************************
You are attempting to build with the incorrect version
of java.
 
Your version is: java version "1.6.0_18".
The correct version is: 1.5.
 
Please follow the machine setup instructions at
    http://source.android.com/download
************************************************************
build/core/main.mk:111: *** stop.  Stop.


```
I found out that sprint has actually released an update to get android 2.1, but it seems to only be for windows right now, so if anyone knows how to get this working using linux, a functioning tutorial would be fantastic.

---

