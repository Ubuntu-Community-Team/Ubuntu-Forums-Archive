---
title: "no boot without usb stick after ubuntu install on stick"
date: 2009-07-01
forum: General Help
---

### Post by EdwardTheThird on 2009-07-01
Hi,

I have a XP computer, and recently installed ubuntu on a USB key.  It works great, except that I cannot boot XP or Ubuntu if the USB stick is not present.
I think the MBR has been overwritten to check the USB key (where the bootloader is saved).  Is this correct?  If not, can someone explain the situation...
And more important: I'm looking for a good solution so that XP can boot without the usb key.  And if I plug the USB key, that I can boot ubuntu.

I read some articles to overwrite the MBR with 'dd ...' , or adjust the MBR with supergrub, but don't know what's the best way to do this.  Can this ubuntu installation be undone, restoring the MBR as it was?

Thanks for any help...

---

### Post by colau on 2009-07-01
> **EdwardTheThird said:**
> Hi,

I have a XP computer, and recently installed ubuntu on a USB key.  It works great, except that I cannot boot XP or Ubuntu if the USB stick is not present.
I think the MBR has been overwritten to check the USB key (where the bootloader is saved).  Is this correct?  If not, can someone explain the situation...
And more important: I'm looking for a good solution so that XP can boot without the usb key.  And if I plug the USB key, that I can boot ubuntu.

I read some articles to overwrite the MBR with 'dd ...' , or adjust the MBR with supergrub, but don't know what's the best way to do this.  Can this ubuntu installation be undone, restoring the MBR as it was?

Thanks for any help...
What's the first boot device?
Check from bios?
Is it intel motherboard?

---

### Post by EdwardTheThird on 2009-07-01
> **colau said:**
> What's the first boot priority device?

i've set the first boot device to the 1st HD...

---

