---
title: "update-grub not working"
date: 2011-05-07
forum: General Help
---

### Post by torabian02 on 2011-05-07
Ok, so I have a copy of 11.04 (/dev/sda3) and a copy of 10.04 (/dev/sda1)
fdisk -l shows /dev/sda1 as boot device.

If I mount /dev/sda1 and look in grub.cfg it has the old entries that I do not want to boot from (it puts an entry in for /dev/sda3 but selected the old kernel somehow (I guess a quirk of doing an upgrade).

So can someone please tell me what the best way is to update grub2 to the correct images and make sure it ever boots again?

---

### Post by satanselbow on 2011-05-07
> **torabian02 said:**
> 

So can someone please tell me what the best way is to update grub2 to the correct images and make sure it ever boots again?

Open a Terminal:

```
sudo update-grub
```

It will pick up all your installed distros ;)

---

