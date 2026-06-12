---
title: "How to make BLUETOOTH SERVICE disabled at startup!"
date: 2011-06-05
forum: General Help
---

### Post by gnome1919 on 2011-06-05
Hi buddies;

I have recently installed Lubuntu 11.04 on an old system. the problem is that it hangs at startup when tries to "Starting Bluetooth". I have searched through this forum and the web and it seems that the problem has something to do with my TV Card. But I can't remove the card because it is a part of my Graphic Card which is an "ATI Radeon 8500DV All In Wonder". I can start the machine with Lubuntu Live CD, and so I thought that maybe I can change a value in a file from installed Lubuntu through Live session that makes the Bluetooth Service disabled at startup. Is it possible? If it is, please walk me through the procedure to do that cause I'm new to Linux and don't know how to do it. :confused::P

Thanks in advance

---

### Post by gnome1919 on 2011-06-06
No idea, huh? :(

---

### Post by ram0042 on 2011-06-06
> **gnome1919 said:**
> Hi buddies;

I have recently installed Lubuntu 11.04 on an old system. the problem is that it hangs at startup when tries to "Starting Bluetooth". I have searched through this forum and the web and it seems that the problem has something to do with my TV Card. But I can't remove the card because it is a part of my Graphic Card which is an "ATI Radeon 8500DV All In Wonder". I can start the machine with Lubuntu Live CD, and so I thought that maybe I can change a value in a file from installed Lubuntu through Live session that makes the Bluetooth Service disabled at startup. Is it possible? If it is, please walk me through the procedure to do that cause I'm new to Linux and don't know how to do it. :confused::P

Thanks in advance
It is sometimes better to remove it using Synaptic but if you just want to disable it:

go to the top right power icon and go to system settings

then startup programs and uncheck Bluetoo[B]th

EDIT:[/B] I forgot your on LXDE right? Can you modify your autostart.sh (located at your ~/.config/openbox)?

---

### Post by mikewhatever on 2011-06-06
If you never use BlueTooth, consider disabling it permanently in the BIOS or uninstalling the relevant packages. Another way to disable it is to blacklist it's module. If you want to do it that way, look at the output of **lsmod**. The modules are usually **btusb** and **bluetooth**, so after confirming that that's the case, add them to /etc/modprobe.d/backlist.conf.

---

### Post by admaen on 2012-01-27
To disable bluetooth service startup:

vi /etc/defaults/bluetooth

change 
BLUETOOTH_ENABLE=1
to
BLUETOOTH_ENABLE=0

(or add "exit 0;" as second line in /etc/init.d/bluetooth)

---

