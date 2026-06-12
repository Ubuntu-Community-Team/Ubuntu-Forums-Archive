---
title: "How can I learn Ubuntu? :)  BackTrack Gnome Installation?"
date: 2011-08-02
forum: General Help
---

### Post by estimate on 2011-08-02
I recently just downloaded And Installed Linux, I really want to learn in it but it is all so hard... :( where can I watch tutorials? 

Second: I downloaded Backtrack 5 Gnome Package. (Direct Download)
Source: [http://www.backtrack-linux.org/downloads/](http://www.backtrack-linux.org/downloads/)

And I've Been trying to Install it and I have no flipping Idea what to do... :(
It was a Zip file so I extracted it... with some app I got.
and now my my folder have some icons and a read me file.. I read the Read me file and I have no fricking Idea.. PLease help :( :( sorry noob...
```
BackTrack 5 ARM Edition Quick Start

This image has been developed and tested on the Motorola Xoom. Your mileage may vary on other devices.
As this image runs in a chroot, you will need to have your device rooted. There are numerous tutorials on the subject online and are not included here.

***Rooting your device will potentially void its warranty and we are not in any way resposible if you brick your device while rooting it.***

### IMPORTANT POINTS ###

1. Since the image runs in a chroot, there is no root password set.
2. There are 2 scripts under /usr/bin/ 'startvnc' and 'stopvnc' that are set to start with the Xoom's default resolution.
3. The current vnc password is set to 'toortoor' and can be changed by running 'vncpasswd'
4. This image is a work in progress and suggestions/tips from the community are always welcome.

### GETTING STARTED ###

1. Once you have downloaded the ARM BT package, save the files in a convenient location. The steps below assume they are in the platform-tools folder of the Android SDK.

2. Go to your platform-tools directory and proceed to make a directory on the device to store BT5:
    ./adb shell
    mkdir /sdcard/BT5
    exit

3. Copy over the busybox install files:
    ./adb push busybox /sdcard/
    ./adb push installbusybox.sh /sdcard

4. Install busybox on the device:
    ./adb shell
    cd /sdcard/
    sh installbusybox.sh
    exit

5. Transfer the required BT5 files to the device:
    ./adb push fsrw /sdcard/BT5/
    ./adb push mountonly /sdcard/BT5/
    ./adb push bootbt /sdcard/BT5/
    ./adb push bt5.img.gz /sdcard/BT5/
    ./adb push unionfs /sdcard/BT5/

6. Uncompress the image and start BT5:
    ./adb shell
    su
    cd /sdcard/BT5
    gunzip bt5.img.gz
    sh bootbt

If all goes well, you'll be in the BT5 chroot:

# sh bootbt
net.ipv4.ip_forward = 1
root@localhost:/# ls /pentest/
backdoors  database     exploits   passwords  scanners  stressing  voip
cisco      enumeration  forensics  python     sniffers  tunneling  web
root@localhost:/#
```
How please help help :( im dreaking out here :(

---

### Post by bodhi.zazen on 2011-08-02
From your post I would suggest you start by running Ubuntu live for a bit.

When you are ready, here is how to install Ubuntu

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Once you are comfortable you can try BT, but it is hard to find documentation for many of the tools in BT and such tools are moderately advanced.

Edit BT also has a graphical installer

[http://www.backtrack-linux.org/tutorials/backtrack-hard-drive-install/](http://www.backtrack-linux.org/tutorials/backtrack-hard-drive-install/)

Not sure what you downloaded exactly.

---

