---
title: "udev Autorun Rule Runs Script Infinitely"
date: 2012-04-16
forum: General Help
---

### Post by abyrne on 2012-04-16
Hi all,

 I have a headless home server running Ubuntu Server 11.10 that has been having a little trouble with networking lately. Since the only way to access this server is with SSH, I wanted to make sure there was a way to roll back my changes if the server looses network access. I decided to do this with a udev rule that executes a script when a certain USB drive is plugged in. 
My rule (located in /etc/udev/rules.d/100-usb-hotplug.rules) looks like this
```
ACTION=="add", ATTRS{idVendor}=="0781", ATTRS{idProduct}=="5150", RUN+="/root/usb_hotplug.sh"
```

The target script (/root/usb_hotplug.sh) looks like this
```
#!/bin/bash
# USB Autorun Script
# Runs when a HOTPLUG is attached and runs the autorun.sh script on that drive.

#Let the user know the script is about to be run
beep -f 1000

#Let the system recognize the drive
sleep 3

#Mount the drive
sudo mount -L HOTPLUG /root/mnt

#Run the script
sh /root/mnt/autorun.sh

#Notify the user with a completion tone
beep -f 1000 -n -f 2000 -n -f 1500

#Unmount the drive
umount /root/mnt

#Make sure udev doesn't run us in an endless loop
#NOTE: We still get stuck in a loop anyway :(
sleep 3

#Bye
exit 0
```

When the drive is plugged in, the script runs correctly. However, the issue is that the script doesn't stop running. I keep hearing the beeps until I unplug the drive. 

Is there a way to stop the script from running in an infinite loop?

Thank you in advanced for your help.

---

### Post by abyrne on 2012-04-17
Bump. Anyone?

---

### Post by abyrne on 2012-04-17
Not a clue?

---

### Post by HiImTye on 2012-04-17
make a global variable and make the script depend on the nonexistence of that global variable

make the global variable cleared after a certain period of time with another script or within the same script

---

### Post by abyrne on 2012-04-17
> **HiImTye said:**
> make a global variable and make the script depend on the nonexistence of that global variable

make the global variable cleared after a certain period of time with another script or within the same script
Thank for your response. Unfortunately, I've already tried that by creating a lockfile in /tmp when the script is run for the first time, and then using another udev rule to remove that lock. However, the removal udev event never triggers for some reason (I've tried using ENV{ID_FS_LABEL}=="HOTPLUG" in the removal rule instead of ATTRS, but it still doesn't work).

Am I missing something here? Is this some kind of weird bug in udev?

---

