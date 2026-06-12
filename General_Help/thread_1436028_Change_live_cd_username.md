---
title: "Change live cd username"
date: 2010-03-22
forum: General Help
---

### Post by Jenkins1 on 2010-03-22
Hi,

I have been trying to change the user name of the live cd.
I have edited the /etc/casper.conf file in the chroot environment but when i run the cd ubuntu is still the user name.

Where should i change it?

Thanks

---

### Post by Jenkins1 on 2010-03-23
bump

---

### Post by Jenkins1 on 2010-03-26
bump please someone must know how it would be a great feature for the disk

---

### Post by TheWeirdness666 on 2011-10-10
Hope this isn't to late for the OP, you need to edit the etc/casper.conf INSIDE the initrd.lz file located on the disc, in the casper folder. So extract the initrd.lz and then edit the file, then repack and replace initrd.lz on the disc, rebuild iso. Took me a while to figure it out, but I was persistent and patient with it

---

