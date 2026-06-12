---
title: "Safe to resize an unused boot partition?"
date: 2011-03-04
forum: General Help
---

### Post by bodselecta on 2011-03-04
Is it safe to resize a partition which is marked as a boot partition?
Is it just a flag i can ignore?

I have ubuntu in an extended partition, the previous partition I've formatted and want to shrink/then move+resize the extended partition to give ubuntu more space.
I was about to resize+move from the gparted usb, when it warned moving a boot partition can cause your system not to start....

I've already created 97gb unallocated space (probably too much) and sda3 is flagged as boot even though it's a formatted empty partition. 

If I'm trying to move/expand sda4 is the warning because of the boot partition on sda4, the facts sda3 is flagged as boot or because the grub stage 2 file is being moved?

---

### Post by YesWeCan on 2011-03-04
Hi. That partition used to be Windows, right? Grub doesn't care about the boot flag so you can delete that partition.
The Windows MBR code (now replaced by grub code) uses the boot flag to choose which Windows installation to boot.

---

### Post by bodselecta on 2011-03-04
Thanks, yes that's the old windows partition. I thought i'd read the boot flag wasn't important.
Is that the cause of the severe warning when running gparted to resize and move sda4?

I basically just want more space for the linux logical partition sda6.


> **YesWeCan said:**
> Hi. That partition used to be Windows, right? Grub doesn't care about the boot flag so you can delete that partition.
The Windows MBR code (now replaced by grub code) uses the boot flag to choose which Windows installation to boot.

---

### Post by YesWeCan on 2011-03-04
I am not sure whether moving the start of sda4 will cripple grub or not. I suppose it depends how the core.img program (located immediately after the MBR) goes about locating /boot/grub.
In the worst case you'll have to reinstall grub and that's easy.

---

### Post by bodselecta on 2011-03-04
Am I doing the wrong thing by wanting to move and expand the extended partition instead of just mounting sda3?

Ubuntu docs say it's better to have home on a different partititon, I'm really just doing this for virtualbox so I have more disk space for vm's.
Rather than try resize the linux logical partition, is it better just to mount?

(cheers for your help)

---

### Post by YesWeCan on 2011-03-04
I don't know.
I have no experience of expanding the root partition. You may want to wait for a second opinion. :)
While you are waiting it would be prudent to back up any important data.

---

### Post by bodselecta on 2011-03-05
Ok, thanks YWC

---

### Post by Mark Phelps on 2011-03-05
While it may be "better" to have the Linux boot directory and files on their own partition, this is certainly not needed.

As long as you don't move the boot partition, resizing it should have no effect.

---

