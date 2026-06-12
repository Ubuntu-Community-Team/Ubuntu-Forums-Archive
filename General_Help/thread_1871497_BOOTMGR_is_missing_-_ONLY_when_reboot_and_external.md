---
title: "BOOTMGR is missing - ONLY when reboot and external HD is on"
date: 2011-10-29
forum: General Help
---

### Post by altjx on 2011-10-29
I formatted my external HD earlier using NTFS. Now, for some reason, when I reboot my machine while my external HD is turned on, it gives me an error saying "BOOTMGR is missing" and it tells me to press ctrl + alt + del to restart...

Did I format my external HD using the wrong filesystem or something?

---

### Post by lightwarrior on 2011-10-29
You need to change your boot device order.

Go to BIOS (at power on)

Locate Boot Device Order
Move order and put first internal HDD
USB or external HDD should be after.

When you boot, bios will look for internal disk first.

---

### Post by altjx on 2011-10-29
Blah, simple. Can't believe I missed that, heh. Thanks.

---

### Post by lightwarrior on 2011-10-29
You're welcome.
Good it was simple ;)
BOOT errors are scary if unexpected.

---

### Post by altjx on 2011-10-29
Indeed. Especially when it comes to linux :)

---

### Post by oldfred on 2011-10-29
But Bootmgr is a Windows 7/Vista file.:)

---

### Post by altjx on 2011-10-29
> **oldfred said:**
> But Bootmgr is a Windows 7/Vista file.:)

Yes, but since I forgot about the boot sequence, I thought maybe GRUB wasn't working anymore and thought maybe it didn't format the entire drive like it was supposed to.

---

