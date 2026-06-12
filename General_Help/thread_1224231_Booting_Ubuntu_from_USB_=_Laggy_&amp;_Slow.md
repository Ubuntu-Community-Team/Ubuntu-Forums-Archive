---
title: "Booting Ubuntu from USB = Laggy &amp; Slow"
date: 2009-07-27
forum: General Help
---

### Post by paul.maddox on 2009-07-27
Hi all,

I've recently installed Ubuntu 9.04 to a 4GB USB2.0 flash memory stick but am finding the performance isn't too great. I'm getting an awful lot of lag and applications frequently locking up for 10-15secs every few minutes. I'm not running compiz or any fancy graphical stuff, just plain gnome.

The PC has a T2400 (1.83GHz dualcore) CPU and 1GB RAM (~746MB used). I'm not noticing any swapping but looking at top I am getting quite a bit of IO wait.

```

paul.maddox@paul-usb:/sys/bus/usb/devices/1-1$ cat product speed version
USB Flash Memory
480
2.00

```


What gives? I assumed running from a USB stick would be faster than HDD! This same machine performed great running from a 2.5" SATA disk even with compiz enabled.

Has anyone seen anything similar?

---

### Post by zarqoon on 2009-07-27
I've yet to see an USB stick that has a read write performance that is even remotely close to a hard disk.
Most sticks write at about 4mb/s and read at about 8mb/s.
The 480mbit speed is just the theoretical speed of the usb 2.0 interface. The Controller reading and writing the flash memory is usually quite slow.
If you really want speed you have to buy a ssd. They are not without reason 10 times more expensive than a stick of the same size.

---

### Post by Mighty_Joe on 2009-07-27
> **zarqoon said:**
> I've yet to see an USB stick that has a read write performance that is even remotely close to a hard disk.


What he said.
There is a lot you can do to increase the performance of your install.  If you installed Ubuntu using the [Live USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator"), it is going to be slow.  The Live CD image is compressed, so there is the constant overhead of that to deal with.
If you did a full install to your flash drive, it's going to be faster than the Live CD, but you can still improve it.
If you created a swap partition, don't use it. Having applications hit the swap partition when you still have memory free is using up valuable USB throughput. Edit your /etc/sysctl.conf file and add the line:
```
vm.swappiness=0
```
See my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680") for some other configuration instructions, like how to move /var into /tmpfs rather than your physical drive.

---

