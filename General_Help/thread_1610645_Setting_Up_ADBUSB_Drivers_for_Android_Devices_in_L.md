---
title: "Setting Up ADB/USB Drivers for Android Devices in Linux (Ubuntu) 10.10?"
date: 2010-10-31
forum: General Help
---

### Post by thisisspeedy on 2010-10-31
Please help I followed this instructions from [http://esausilva.com/2010/05/13/setting-up-adbusb-drivers-for-android-devices-in-linux-ubuntu/](http://esausilva.com/2010/05/13/setting-up-adbusb-drivers-for-android-devices-in-linux-ubuntu/)

> Download the latest Android SDK from Google: Android SDK
Extract the TGZ file to your home/user directory
NOTE: User would be your username
On your phone, click Settings > Applications > Development and make sure USB Debugging is on.
Login as root and create this file: /etc/udev/rules.d/##-android.rules
NOTE: In the above file replace ## with the number 50 if you are running Gusty/Hardy/Dapper (50-android.rules) or with the number 70 if you are running Karmic Koala/Lucid Lynx(70-android.rules)
Or simply type in terminal sudo gedit /etc/udev/rules.d/##-android.rules then enter your password
The file should read:
For Gusty/Hardy: SUBSYSTEM==”usb”, SYSFS{idVendor}==”0bb4&#8243;, MODE=”0666&#8243;
For Dapper: SUBSYSTEM==”usb_device”, SYSFS{idVendor}==”0bb4&#8243;, MODE=”0666&#8243;
For Karmic Koala: SUBSYSTEM==”usb”, SYSFS{idVendor}==”0bb4&#8243;, MODE=”0666&#8243;
For Lucid: SUBSYSTEM==”usb”, SYSFS{idVendor}==”0bb4&#8243;, MODE=”0666&#8243;
NOTE: In the above lines the code ”0bb4&#8243; refers to a HTC device. If your phone is from a different manufacturer, replace the code with the appropriate from the table below.

Execute: sudo chmod a+rx /etc/udev/rules.d/70-android.rules
Reboot
To run ADB you need to add an environment variable to your bashrc file:
Open a terminal window and type: sudo gedit .bashrc
Add the following line at the end: export PATH=${PATH}:~/home/user/android-sdk-linux_86/tools
Save and close
You should be ready to go, type adb devices in a terminal window with your phone plugged in.
If you see a serial number pop up that means you are done. Should look something like this:
List of devices attached
HT99PHF02521 device
If for some reasons when running adb devices gives you a “no permissions” error, try typing the following in terminal
adb kill-server
adb start-server
USB Vendor IDs

MANUFACTURER	USB VENDOR ID
Acer	0502
Dell	413c
Foxconn	0489
Garmin-Asus	091E
HTC	0bb4
Huawei	12d1
Kyocera	0482
LG	1004
Motorola	22b8
Nvidia	0955
Pantech	10A9
Samsung	04e8
Sharp	04dd
Sony Ericsson	0fce
ZTE	19D2
Common ADB Commands

- Lists which devices are currently attached to your computer

adb devices
- Drops you into a basic linux command shell on your phone with no parameters, or lets you run commands directly

adb shell
- Lets you install an Android application on your phone

adb install
- Remounts your system in write mode – this lets you alter system files on your phone using ADB

adb remount
- Rets you upload files to your phones filesystem

adb push
- Lets you download files off your phones filesystem

adb pull
- Starts dumping debugging information from your handset to the console – useful for debugging your apps

adb logcat

My problem is that they don't have instructions for Maverick. 

when I run > sudo gedit /etc/udev/rules.d/##-android.rules it bring up a empty file. 

Please help.

---

### Post by gcurchod on 2010-11-01
It says:

> NOTE: In the above file replace ## with the number 50 if you are running Gusty/Hardy/Dapper (50-android.rules) or with the number 70 if you are running Karmic Koala/Lucid Lynx(70-android.rules)

Which means: according to your version of Ubuntu, create a file named 50-android.rules or 70-android.rules. This file is indeed empty, because you just created it.

Then pick the right line (related to your version of Ubuntu). For example, with Gusty or Hardy, pick:
```
SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
```
Copy this line in the file your created before (beware of the quotes, you might need to retype them).
If you do not have an HTC device, change the "0bb4" with the right code.
When you're finished, save and close

Change the mode of the file using the "chmod" command as described in the post.


After rebooting, your device should be recognized (try command "adb devices").
This worked for me.


Regards

---

### Post by thisisspeedy on 2010-11-01
I really appreciate your response thanks.

---

### Post by thisisspeedy on 2010-11-01
So remove the quotes as well?

---

### Post by gcurchod on 2010-11-01
I had to type them again in the file because their were special quotes...
Just (manually) type the line directly in the text file so you won't have this problem.

---

### Post by thisisspeedy on 2010-11-01
> **gcurchod said:**
> I had to type them again in the file because their were special quotes...
Just (manually) type the line directly in the text file so you won't have this problem.So you were able to do this on your phone?

After I run sudo chmod a+rx /etc/udev/rules.d/70-android.rules how long should I wait to reboot the PC?

After I run abd devices I get adb devices
No command &#8216;adb&#8217; found, did you mean:
Command &#8216;cdb&#8217; from package &#8216;tinycdb&#8217; (main)
Command &#8216;gdb&#8217; from package &#8216;gdb&#8217; (main)
Command &#8216;dab&#8217; from package &#8216;bsdgames&#8217; (universe)
Command &#8216;zdb&#8217; from package &#8216;zfs-fuse&#8217; (universe)
Command &#8216;mdb&#8217; from package &#8216;mono-debugger&#8217; (universe)
Command &#8216;tdb&#8217; from package &#8216;tads2-dev&#8217; (multiverse)
Command &#8216;pdb&#8217; from package &#8216;python&#8217; (main)
Command &#8216;jdb&#8217; from package &#8216;openjdk-6-jdk&#8217; (main)
Command &#8216;ab&#8217; from package &#8216;apache2-utils&#8217; (main)
Command &#8216;ad&#8217; from package &#8216;netatalk&#8217; (universe)
adb: command not found

---

### Post by gcurchod on 2010-11-01
As I said:
> This worked for me.


> How long should I wait to reboot the PC?
Why would you wait? Don't wait!


> After I run abd devices I get adb devices
(...)
adb: **command not found**
That means Linux can't find "adb"... You'll find the solution hear: [http://www.howtoforge.com/installing-google-android-sdk1.0-on-ubuntu8.04-desktop-p2]("http://www.howtoforge.com/installing-google-android-sdk1.0-on-ubuntu8.04-desktop-p2")

---

### Post by thisisspeedy on 2010-11-01
Thanks for your help. But I am lost right now. It still not. That link you sent it's outdated it seems like.

---

### Post by gcurchod on 2010-11-01
Sorry, cannot help you more...

I'm afraid you ask questions that are already answered here:
[http://esausilva.com/2010/05/13/setting-up-adbusb-drivers-for-android-devices-in-linux-ubuntu/]("http://esausilva.com/2010/05/13/setting-up-adbusb-drivers-for-android-devices-in-linux-ubuntu/")

You obviously didn't do point 8... Please read this tuto again.


Regards

---

### Post by thisisspeedy on 2010-11-01
now when I type sudo gedit .bashrc I get bash: syntax error near unexpected token `do'

so now its different

---

### Post by sprotch on 2010-11-02
>> now when I type sudo gedit .bashrc I get bash: syntax error near unexpected token `do'

A few points...
1. Verify you have gedit installed! If you are on Ubuntu 10.10 it will be installed. If you are on a different flavor (Kubuntu, Xubuntu,...) you should use a different editor available on your distro.
2. Verify that you are in your home directory! If you are not in your home directory give the full path to your .bashrc (~/.bashrc).
3. Do not copy the command from this webpage and paste it in your terminal. HTML has sometimes weird formatting for special characters (space, ...) which are not correctly interpreted by the terminal. Type manually the command in your terminal.

4. Last and not least. **Learn Linux and its internals a bit more deeply before trying to "hack" your phone!** Not knowing and understanding what you do can be really dangerous and brick your phone if you do not carefully pay attention to every command you perform!

---

### Post by thisisspeedy on 2010-11-03
Thanks again but when I type in (~/.bashrc) it says Permission denied

---

