---
title: "Change load order b/w ehci-hcd, uhci-hcd and ohci-hcd?"
date: 2010-07-03
forum: General Help
---

### Post by Krovas on 2010-07-03
I'm having extreme difficulty getting my external SATA drive to mount for any substantial length of time. It spins and sputters and mounts for a few seconds before being snatched away again. After some research, it sounds very much like this issue is the culprit (as elucidated by no less august personage than Alan Stern):


[http://lkml.org/lkml/2008/10/24/209](http://lkml.org/lkml/2008/10/24/209)

> On Thu, 23 Oct 2008, Larry Finger wrote:

> In my system, a number of messages that state "unable to enumerate USB device"
> are logged. These are intermittent and likely due to some race condition
> at bootup.
> 
> Some of these happen when the EHCI driver is loaded after UHCI or OHCI, which
> causes the device to be switched away from the other controller that's trying
> to enumerate it, at least momentarily. This type of message is logged at most
> once for each hub and occurs in about 70% of my reboots.

This is normal; it is caused by userspace loading the drivers in the
wrong order.  ehci-hcd is supposed to be loaded before uhci-hcd or
ohci-hcd, not after.  There's no point trying to change the kernel to
avoid it.

> A more insidious form of the message occurs hundreds of times in about 10% of
> reboots. They continue until the system is rebooted. This patch limits the
> number of these messages to 20. Once the actual cause of this message is
> located, this patch can be reverted.

I would prefer to attack this problem directly rather than wallpaper 
over it.  Can you provide more information?  For example, a dmesg log 
with CONFIG_USB_DEBUG and CONFIG_PRINTK_TIME enabled would help.  It 
might also help to know what the devices which can't be enumerated 
actually are.

Alan Stern



The trouble is, what can I do about it? How does one change the order in which modules load in Ubuntu?

---

### Post by dino99 on 2010-07-03
hey have you noted the date of this comment ? Now its old story and has been fixed by kernel team.

your trouble can be due to missing received power: look at your hardware specs (how much power does it need to run smootly) and forum support. (usb limitations)

sudo update-usbids && sudo update-pciids

you might find usefull errors logged too to help you go ahead

---

### Post by Krovas on 2010-07-03
> **dino99 said:**
> hey have you noted the date of this comment ? Now its old story and has been fixed by kernel team.


Has it? 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256767](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256767)

This is precisely the behavior exhibited by my drive, except that it doesn't work but about five seconds at a time. The device as an extra plug to draw additional power, but it makes no difference.

---

