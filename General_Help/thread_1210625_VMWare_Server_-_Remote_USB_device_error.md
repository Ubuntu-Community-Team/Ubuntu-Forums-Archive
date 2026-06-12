---
title: "VMWare Server - Remote USB device error"
date: 2009-07-11
forum: General Help
---

### Post by fermulator on 2009-07-11
I'm having a problem with VMWare & USB devices.

**_Setup:_**
 * Host OS: Ubuntu Jaunty
 * VMWare Server: 2.0.1
 * Guest OS: Windows XP Pro

**_The Problem:_**

Using VMWare's interface, one is supposed to be able to 'passthrough' a USB device to the guest OS.  This allows things like scanners, printers, usb keys etc. to be used in the guest OS.  This is completed by Choosing "Devices --> device_name --> Connect".

When I try this however, I receive the following error:
> **Remote USB device error: Remote device disconnected: an error occured while sending data.**

The only other help I've found is on the VMWare forums here: [http://communities.vmware.com/thread/188161]("http://communities.vmware.com/thread/188161")  Unfortunately though, the last two posts (which sound like they address the problem), don't work on Ubuntu.  I believe Ubuntu's udev for USB is a little different now?

Any tips would be most appreciated.
Thanks!

---

### Post by fermulator on 2009-07-24
bump (sorry!)

---

### Post by LeoLex on 2009-07-26
Same issue here. Is there any solution?

---

### Post by fermulator on 2009-07-30
> **LeoLex said:**
> Same issue here. Is there any solution?

Still no solution as far as I know ... :-(

---

### Post by Bernman93 on 2009-08-06
I found this solution on another thread, and it does work with Jaunty.

In the file /etc/fstab

You add the following lines

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Reboot, and you should be able to pass usb filesystems to the guest OS.  Funny, but it does only seem to affect filesystem devices, as I have been able to set up and run my USB printer fine before I fixed this.

Good Luck

---

### Post by dcstar on 2009-08-07
> **Bernman93 said:**
> I found this solution on another thread, and it does work with Jaunty.
..........
Good Luck

And last time I looked this, and many other solutions, was in the Virtualization forum (with all the other VM info).

---

### Post by fermulator on 2009-08-08
> **Bernman93 said:**
> I found this solution on another thread, and it does work with Jaunty.

In the file /etc/fstab

You add the following lines

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Reboot, and you should be able to pass usb filesystems to the guest OS.  Funny, but it does only seem to affect filesystem devices, as I have been able to set up and run my USB printer fine before I fixed this.

Good Luck

This worked for me!
PS:, you don't have to reboot, simply:
```
sudo mount -a -t usbfs
```

---

### Post by digital_sabine on 2009-08-14
I just wanted to say THANK YOU--this solution worked PERFECTLY for me!  Kudos.  Never would have worked this out on my own.

ETA: I had to restart the machine in order to get it to work. the sudo mount command did not do it for me.  Very minor!

---

### Post by darcmann on 2009-12-28
Thanks for this.  Worked great. Very helpful!

---

