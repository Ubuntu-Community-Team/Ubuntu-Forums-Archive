---
title: "lsusb won't find hard drive after boot"
date: 2010-02-24
forum: General Help
---

### Post by wookiefoot on 2010-02-24
I've been having some trouble getting my two external USB hard drives to mount on boot. They are not recognized by lsusb after a boot, but after they are power cycled or unplugged & replugged they will show up in lsusb and mount. 

One odd thing I noticed was that when one of the drives was moved to a different port before booting it would be recognized for that boot only:confused:

I have tried adding usb_storage to /etc/modules and doing a update-initramfs to my kernel (2.6.31-14) to no avail.

Since I started having this problem, I have reinstalled ubuntu on a different internal drive, and this did not fix it.

I'm not sure if this matters, but the UUIDs of the two drives are identical. I would try reformatting one of them but its quite inconvenient. My /etc/fstab is set up to mount them using their labels (ex1 and ex2) rather than the UUID, and I can mount them both at the same time. 

Does anyone know of a fix? Thanks in advance.

---

### Post by gsmanners on 2010-02-24
The UUIDs being identical could be messing it up. If they are formatted ext2/3/4 you could modify their UUIDs with this:

sudo tune2fs -U random /dev/whatever

---

### Post by wookiefoot on 2010-02-25
I just reformatted one of the drives and now they have different UUIDs. I am still having the same problem. I think the issue is that they aren't getting recognized as USB devices on boot rather than the way they are set up. Any ideas?

---

### Post by booshire on 2010-02-25
> **wookiefoot said:**
> I just reformatted one of the drives and now they have different UUIDs. I am still having the same problem. I think the issue is that they aren't getting recognized as USB devices on boot rather than the way they are set up. Any ideas?

Not pointing fingers or saying this is your issue, but I only have this problem when I do not unmount the drive before removing it.

---

### Post by wookiefoot on 2010-02-25
I'm not removing the drives at all. They are already plugged in & recognized and upon rebooting they are no longer recognized. I'm assuming rebooting will unmount the drives before power cycling. They will only be recognized if I plug them in while ubuntu is already running, except when I swap ports before booting, as I mentioned before. 
I've set up auto-mounting on the windows partition of my other machine (identical ubuntu installation) & it works just fine without having to unmount it before rebooting, so I don't think thats the issue.

---

### Post by wookiefoot on 2010-02-25
When I remove either of the drives and plug it into a different computer (running an identical Ubuntu installation), it does not mount. Could the first computer be having issues with fully unmounting the drives? This would also seem to explain why they aren't recognized on boot.

---

