---
title: "iPod is not detected"
date: 2011-01-14
forum: General Help
---

### Post by JThompson118 on 2011-01-14
I just plugged my iPod classic into my desktop that's running 10.04. My iPod says it's connected, but my computer has other ideas. Usually a pop-up comes on and asks me if I want to use a program with it (Rhythmbox, etc.). Heck, I was just playing with it earlier today. Any ideas as to what's going on?

---

### Post by CrusaderAD on 2011-01-14
It's something with the drivers that control them. Check out:

[http://ubuntuforums.org/showthread.php?t=1628529&page=2]("http://ubuntuforums.org/showthread.php?t=1628529&page=2")

---

### Post by JThompson118 on 2011-01-14
Checked it out, but everything on there has to deal with the iPhone/iPod Touch upgrades, for the most part (mine isn't a touch). I played around with some things, but to no avail. Why would it work fine one hour, and totally forget how to do something the next, especially if I didn't upgrade or alter anything between that time?

I upgraded my system to 10.10 last night, and it still doesn't register the stupid thing. Weird thing is, my iPod recognizes it, and the computer still charges the device. my girlfriend's laptop reads it fine, so I know it's not the device.

---

### Post by JThompson118 on 2011-01-14
Checked it out, but everything on there has to deal with the iPhone/iPod Touch upgrades, for the most part (mine isn't a touch). I played around with some things, but to no avail. Why would it work fine one hour, and totally forget how to do something the next, especially if I didn't upgrade or alter anything between that time?

I upgraded my system to 10.10 last night, and it still doesn't register the stupid thing. Weird thing is, my iPod recognizes it, and the computer still charges the device. my girlfriend's laptop reads it fine, so I know it's not the device.

---

### Post by JThompson118 on 2011-01-14
Checked it out, but everything on there has to deal with the iPhone/iPod  Touch upgrades, for the most part (mine isn't a touch). I played around  with some things, but to no avail. Why would it work fine one hour, and  totally forget how to do something the next, especially if I didn't  upgrade or alter anything between that time?

I upgraded my system to 10.10 last night, and it still doesn't register  the stupid thing. Weird thing is, my iPod recognizes it, and the  computer still charges the device. my girlfriend's laptop reads it fine,  so I know it's not the device.

---

### Post by JThompson118 on 2011-01-14
Checked it out, but everything on there has to deal with the iPhone/iPod  Touch upgrades, for the most part (mine isn't a touch). I played around  with some things, but to no avail. Why would it work fine one hour, and  totally forget how to do something the next, especially if I didn't  upgrade or alter anything between that time?

I upgraded my system to 10.10 last night, and it still doesn't register  the stupid thing. Weird thing is, my iPod recognizes it, and the  computer still charges the device. my girlfriend's laptop reads it fine,  so I know it's not the device.

---

### Post by JThompson118 on 2011-01-14
Checked it out, but everything on there has to deal with the iPhone/iPod  Touch upgrades, for the most part (mine isn't a touch). I played around  with some things, but to no avail. Why would it work fine one hour, and  totally forget how to do something the next, especially if I didn't  upgrade or alter anything between that time?

I upgraded my system to 10.10 last night, and it still doesn't register  the stupid thing. Weird thing is, my iPod recognizes it, and the  computer still charges the device. my girlfriend's laptop reads it fine,  so I know it's not the device.

---

### Post by JThompson118 on 2011-01-14
Checked it out, but everything on there has to deal with the iPhone/iPod  Touch upgrades, for the most part (mine isn't a touch). I played around  with some things, but to no avail. Why would it work fine one hour, and  totally forget how to do something the next, especially if I didn't  upgrade or alter anything between that time?

I upgraded my system to 10.10 last night, and it still doesn't register  the stupid thing. Weird thing is, my iPod recognizes it, and the  computer still charges the device. my girlfriend's laptop reads it fine,  so I know it's not the device.

---

### Post by CrusaderAD on 2011-01-14
Did you try installing the latest version of libmobiledevice? I think they use the same logic.

---

### Post by JThompson118 on 2011-01-14
Yeah, that's all installed and upgraded.

---

### Post by CrusaderAD on 2011-01-14
It's a long shot, but did you try a different usb slot? Maybe it's the slot on the machine itself. Maybe the wire? Does nothing come up, even in Nautilus?

---

### Post by JThompson118 on 2011-01-15
Yeah, I've tried it in all slots. And nothing reads it; I can't even access it in the "computer" folder.

---

### Post by CrusaderAD on 2011-01-17
What's the output of:

```
lsusb
```

This should list it if it's connected.

---

### Post by CrusaderAD on 2011-01-17
What's the output of:

```
lsusb
```

This should list it if it's connected.

---

### Post by CrusaderAD on 2011-01-17
What's the output of:

```
lsusb
```

This should list it if it's connected.

---

### Post by JThompson118 on 2011-01-17
> Bus 001 Device 008: ID 05ac:1261 Apple, Inc. iPod Classic


So it knows my iPod is there, but why can't I access it?

---

### Post by JThompson118 on 2011-01-18
Not sure what happened, but now the iPod mounts properly and is there. However, all programs I use with it (Rhythmbox/gtkpod) crash upon startup.

---

### Post by CrusaderAD on 2011-01-18
strange... maybe the older versions are no longer supported?

---

### Post by stallinux on 2011-10-21
SOLUTION found

Here the same. iPod Classic Video connected via USB to Ubuntu 11.04 32 bit. Nothing happens (on the computer; the iPod signals connection and charging). Yet, on (Administration): Disk Utility the iPod disk is visible but cannot be mounted.
Note: It is running Rockbox, which might be a problem (in recent versions of the Debian kernel; it worked before).

"An error occurred while performing an operation on 'iPod' (Partition 1 of Apple iPod): File system driver not installed"

The disk is shown as 'free' (60 GB) apart from a FAT partition of 115 MB.

On W***os the disks (iPod and floppy) are visible and accessible.

SOLUTION: Restore the device with iTunes.
Now it has two partitions, one 115 MB and one 60 GB

---

