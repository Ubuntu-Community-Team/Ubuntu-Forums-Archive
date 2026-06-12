---
title: "Jpilot - help!"
date: 2006-04-09
forum: General Help
---

### Post by wizzkid on 2006-04-09
I install jpilot to sync with my Treo 650. When I press the "Sync your palm to desktop" I encounter this error:

****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished


Also, I had to run jpilot thru terminal with command sudo jpilot. if I run it thru the menu, it doesnt work. 

Hope you could help me with this.

Thanks.

---

### Post by apolyak on 2006-04-09
I assume that gnome-pilot is installed and you use USB connection.

Read [https://wiki.ubuntu.com/EasyPalmDeviceSetup?highlight=%28palm%29](https://wiki.ubuntu.com/EasyPalmDeviceSetup?highlight=%28palm%29) including notes. 

Add Pilot applet to Panel => right click on Panel (top) and select add to Panel. Scroll down to Utilities and select Pilot Applet.

You can set sync rules System->Preferences->Palm OS Devices
or clicking on Pilot Applet icon on Panel.

This will sync with Evolution.

Some times you may need to restart Pilot Applet - disconnect Palm device, click on Pilot Applet icon on Panel and select restart.

If you want to use jpilot, than delete Pilot Applet icon from Panel. Rules you can set in jpilot preferences. Make sure you press hot sync button on pilot device first, then, after a few seconds click on Sync your palm to desktop in jpilot.

good luck

---

### Post by wizzkid on 2006-04-10
Thanks a lot.

But my evolution have problem :(

After I add account, everything seems okay. but when I restart the evolution the account I just created was gone and bring me the account setup wizzard :( any fix here? 

Thanks

---

### Post by apolyak on 2006-04-11
I didn't have a similar problem with evolution. Try delete directory ~/.evolution. Next time you start evolution that directory must be recreated.
Regards

---

### Post by sendgift2008 on 2006-04-11
[[img]http://www.top22.cn/QQCF_Pic/QQCf_Style12.gif[/img]](http://www.top22.cn/qqcf.asp?46.sendgift2050)

---

### Post by jal on 2006-04-13
[QUOTE=wizzkid]I install jpilot to sync with my Treo 650. When I press the "Sync your palm to desktop" I encounter this error:

****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished


Also, I had to run jpilot thru terminal with command sudo jpilot. if I run it thru the menu, it doesnt work. 

Hope you could help me with this.

Thanks.[/QUOTE]

Sorry, I don't have an answer, but I thought it would help to know that I am experiencing exactly the same symptoms. 

I can get it to start syncing only the first time after re-booting the OS. 
I start the palm sycing first, this seems to create the /dev/pilot (which is defined in the PalmOS devices dialog) as a symlink to /dev/ttyUSB1, and jpilot will use /dev/pilot and start syncing. jpilot displays a message "press hot sync button on pda" but seems to go ahead with the sync anyway.

I've never got it to work twice in a row, I think that the OS is setting up the USB link as /dev/ttyUSB3 /dev/USB4, i.e. the number is incremented on each attempt.

---

### Post by distortedstar on 2007-05-08
I'm having this problem as well. Doesn't work on reboot, either. It worked once...the very first time I ran Jpilot. After that, I just an error.

---

### Post by distortedstar on 2007-05-08
Solved!

In the "device" section in preferences, you should put: "usb:" without quotes. This worked great for me. I also got gnome-pilot up and running, which nice but has an annoying bug involving undated todo items. So, because of that, I'll probably just be sticking with jpilot.

You have to edit /etc/udev/rules.d/10-custom.rules
and put the line

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"


I had to do that to get gnome-pilot working, so I'm not sure if it has anything to do with jpilot or not.

---

### Post by marnom on 2007-05-10
Yes, it worked like a charm for J-Pilot too. Bravo!

---

### Post by mm2ps on 2007-05-19
> **jal said:**
> Sorry, I don't have an answer, but I thought it would help to know that I am experiencing exactly the same symptoms. 

I can get it to start syncing only the first time after re-booting the OS. 
I start the palm sycing first, this seems to create the /dev/pilot (which is defined in the PalmOS devices dialog) as a symlink to /dev/ttyUSB1, and jpilot will use /dev/pilot and start syncing. jpilot displays a message "press hot sync button on pda" but seems to go ahead with the sync anyway.

I've never got it to work twice in a row, I think that the OS is setting up the USB link as /dev/ttyUSB3 /dev/USB4, i.e. the number is incremented on each attempt.

Hi,

I had a similar problem but solved it in my case by changing 

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

to

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="XXXXXXXXXX", MODE="666"

where XXXXXXXXXX is the name you have given your PDA.

Regards,

Douglas

---

