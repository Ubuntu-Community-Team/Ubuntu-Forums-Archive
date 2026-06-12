---
title: "Enable Disable Hardware"
date: 2011-07-19
forum: General Help
---

### Post by DORiANxGRAY on 2011-07-19
Hey all, is there a way to enable/disable specified hardware? 
Allow me to explain, i have 2 wireless adapters, one integrated and one USB, i want to use the USB adapter for 5Ghz 802.11n and the integrated wifi adapter in my system is the one ubuntu is defaulted to.. i have the drivers for the USB device already installed i just need to disable the integrated device. thx in advance.

---

### Post by Bucky Ball on 2011-07-19
Try opening a terminal and:
```

lsmod | grep r8
```You should see the two interface modules there. Copy the name of the one you want disabled. Open:
```

sudo nano /etc/modprobe.d/blacklist.conf
```... and add at the bottom of that file:

```
# Disable my wireless
blacklist (paste the module name you copied before here)
```Reboot and you should be on the usb. Run:

```

sudo lshw -C network
```... to find out. You should see them both, one unused.

---

### Post by DORiANxGRAY on 2011-07-19
It's not saving the etc/modprobe.d/blacklist.conf file after i add the line in there... is there something i'm missing. everything else is working proper.

---

### Post by Bucky Ball on 2011-07-19
You're using sudo first? '**sudo** nano /etc/modprobe.d/blacklist.conf'. Once you make the changes you need to hit:

Ctl+x (to exit)
'y' (to save modified buffer)
Enter (to confirm overwriting the existing file)

... and that should save. If it doesn't there's something very peculiar going on! ;)

---

### Post by paulkiss on 2012-06-08
Thanks, **Bucky Ball**, that helped me to disable Wireless.

Can it be that some modules cannot be disabled? Like, I blacklisted Ethernet hardware (coz I don't need it on my netbook), but it still shows as active and with a kernel driver working with it...

---

### Post by steeldriver on 2012-06-08
if you're using Network Manager (not /etc/network/interfaces) here's a method that has worked for me:

[http://ubuntuforums.org/showthread.php?t=1980051&highlight=unmanaged-devices](http://ubuntuforums.org/showthread.php?t=1980051&highlight=unmanaged-devices)

---

