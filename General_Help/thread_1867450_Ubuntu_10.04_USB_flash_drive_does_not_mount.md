---
title: "Ubuntu 10.04 USB flash drive does not mount"
date: 2011-10-23
forum: General Help
---

### Post by Ralph Hinkley on 2011-10-23
I'm stumped and any help would be greatly appreciated!
I am running Ubuntu 10.04 on a thinkpad T41. I am trying to use a DANE-ELEC 8GB USB flash drive. When I plug it in, the LED flashes like it's trying to mount, but it never shows up.

It does not show up in the "Disk Utility".
I have installed "usbmount" from synaptic package manager.

When I "lsmod | grep usb", I get this:

clay@MrSmith:~$ lsmod | grep usb
usbhid                 36110  0 
hid                    67288  1 usbhid
usb_storage            39841  0 

When I "lspci | grep USB", I get this:

clay@MrSmith:~$ lspci | grep USB
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)

When I "tail -f /var/log/messages" then plug in the drive, I get this over and over again with the address always changing:

Oct 22 23:19:35 MrSmith kernel: [ 4122.752079] usb 1-3: new high speed USB device using ehci_hcd and address 75
Oct 22 23:19:37 MrSmith kernel: [ 4125.132169] usb 1-3: new high speed USB device using ehci_hcd and address 87
Oct 22 23:19:41 MrSmith kernel: [ 4129.024161] usb 1-3: new high speed USB device using ehci_hcd and address 107

I'm afraid I don't know the guts of linux well enough to know exactly what all that means. Many thanks to anyone who can assist.

---

### Post by Ralph Hinkley on 2011-10-23
BTW, the flash drive works fine on my wife's Win7 PC.
Thanks again in advance.

---

### Post by Ralph Hinkley on 2011-10-23
hours later and still no luck. I'm starting to think maybe I just need to buy a different flash drive. I've used plenty of other ones with no problems. Suggestions are still welcome though.

PS. My wife's friend is a Windows fan. She's been harassing me mercilessly over this as a "proof that windows is superior" thing. Please help!!!

---

### Post by mue.de on 2011-10-23
Hello,

I have nearly the same problems at kubuntu 10.04, but i have the problems after trying 'usbmount' and i have it only at one user-account, a fresh installed user has no problems with usb-automounting.
I think usbmount is an old tool that you don't need at Lucid Lynx; it uses 'usb0...7' mount points, whereas the new udev-tool uses 'disk, disk-1,...' ?: I'm no expert in these system-details.

Maybe we can get a more sophisticated answer from anyone else ?

---

### Post by Ralph Hinkley on 2011-10-23
> I think usbmount is an old tool that you don't need at Lucid Lynx; it uses 'usb0...7' mount points, whereas the new udev-tool uses 'disk, disk-1,...' ?: I'm no expert in these system-details.

Maybe we can get a more sophisticated answer from anyone else ?

Yeah. I got nothin'!

---

### Post by Ralph Hinkley on 2011-10-23
bump

---

### Post by Ralph Hinkley on 2011-10-23
Update: I picked up a new flash drive today. It won't mount either. We tried both flash drives in my wife's pc, and both worked. We then tried both in her laptop which is also running Ubuntu 10.04, and both worked! 

So I guess the good news is that that means it's not a problem with Ubuntu. Bad news - Neither work on my thinkpad. So maybe that means it's a BIOS problem??? maybe. I'm wondering if it's a USB1 vs USB2 thing. 

I will continue to research and post my findings in case anyone else has this same problem.

---

### Post by oldtimer7777 on 2011-10-23
Have you tried using:

System >>> Admin >> Startup Disc Creator

Does it locate the flash drive so you can format it that way?

---

### Post by Ralph Hinkley on 2011-10-23
HOLY SWEET MAGOLLI! (That doesn't really mean anything, but I'm trying to keep this thread rated PG.)

I solved it! Turns out this is a Thinkpad problem, not an Ubuntu problem, and I was able to fix it by following these instructions:
> disabling ehci_hcd
If your distribution (like Fedora 11) instead compiled the ehci_hcd support directly into the kernel, you cannot unload or blacklist it.
In such cases you can unbind it in sysfs, but first we need to find what the PCI device number of the EHCI controller is as follows;

```
lspci|grep -i ehci
```

On a ThinkPad T41 this returns

```
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)

```
To unbind the ehci_hcd support from the PCI device, run the following command (adjust PCI location, based on lspci result)

```
echo -n "0000:00:1d.7" > /sys/bus/pci/drivers/ehci_hcd/unbind

```
To automatically unload it on bootup, simply add the last command to /etc/rc.local.


to see the whole article go here:
[http://webcache.googleusercontent.com/search?q=cache:http://www.thinkwiki.org/wiki/Problem_with_USB_2.0](http://webcache.googleusercontent.com/search?q=cache:http://www.thinkwiki.org/wiki/Problem_with_USB_2.0)

I don't know if anyone else out there actually cares, but I for one, am excited and happy to have this issue SOLVED!

---

### Post by eXcEeDe on 2011-12-28
Late reply, I know, but I just want to thank you! This gave me the solution to a problem with udev rules not working on a smart card reader that I have been working an for days...
 
Although I had to use the command
echo -n 0000:00:1d.7 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind
 
Otherwise I got permission issues.
 
Cheers!

---

### Post by TroN-0074 on 2011-12-28
Thank you for posting this. I have a Thinkpad T41 and I havent had usb for a year. For a while I thought it might just be time to retire the thing but I'll try this when I get home this afternoon.

---

