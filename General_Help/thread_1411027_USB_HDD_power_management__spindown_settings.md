---
title: "USB HDD power management / spindown settings"
date: 2010-02-19
forum: General Help
---

### Post by 9tails on 2010-02-19
Please help... I'm looking for a way to change the USB HDD spin down time setting, or to disable USB power management altogether.

Basically, my new Western Digital USB HDD spins down too soon and often. As a result the Load Cycle Count is increasing too fast - four times faster than my 2 years old laptop's drive! ](*,)

I searched the forums and have found this thread:

```
http://ubuntuforums.org/showpost.php?p=5031046&postcount=3
```

it suggests using hdparm -B 255 which did the trick on internal ATA/SATA/SCSI drives... unfortunately it doesn't work on USB HDDs :(

I also tried passing usbcore.autosuspend=-1 as a kernel parameter but it didn't seem to do anything (apart from the fans spinning at max?)

I know there is a configurable /sys/bus/usb/devices/*/power/level but I'm not sure if I'm supposed to change those, or... maybe there is a simpler way.

Any help would be greatly appreciated!

---

### Post by 9tails on 2010-02-19
Nevermind. I managed to disable automatic standby and the usb drive power management (apm) feature, but the load cycles count keeps increasing...

Anyway, in case you're reading this thread looking for a way to disable apm on usb drives, or the automatic spindown feature, here's how I did it.

If you want to disable spindown, run:

sudo sdparm -a /dev/sda
if the STANDBY attribute is set, change it to 0 using sdparm.

If you want to disable apm for an usb drive:

cd /sys/bus/usb/devices

Look for the directories containing a file called "product". If the file contains the string "Portable USB drive" or similar, that's the one you're looking for. Just do a sudo echo "on" > ./power/level and you have disabled apm for that drive.

---

### Post by Guiness6 on 2010-06-02
> **9tails said:**
> Nevermind. I managed to disable automatic standby and the usb drive power management (apm) feature, but the load cycles count keeps increasing...

Anyway, in case you're reading this thread looking for a way to disable apm on usb drives, or the automatic spindown feature, here's how I did it.

If you want to disable spindown, run:

sudo sdparm -a /dev/sda
if the STANDBY attribute is set, change it to 0 using sdparm.

If you want to disable apm for an usb drive:

cd /sys/bus/usb/devices

Look for the directories containing a file called "product". If the file contains the string "Portable USB drive" or similar, that's the one you're looking for. Just do a sudo echo "on" > ./power/level and you have disabled apm for that drive.

Would you mind explaining the last bit more clearly? Do I add that exact line to the product file? If that's a command, I'm fuzzy on what it will do.

*EDIT* I found the autosuspend file was set to 2. I was able to change it to 1 which is supposed to disable that feature. Level was already set to "on". I'm hoping this will take care of the problem. This was helpful!

---

