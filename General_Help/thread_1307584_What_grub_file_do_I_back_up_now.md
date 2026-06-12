---
title: "What grub file do I back up now?"
date: 2009-10-31
forum: General Help
---

### Post by Rytron on 2009-10-31
Hi.

In previous Ubuntu releases up to Ubuntu 9.10 I would do

```
sudo mkdir /etc/Master_Copies
sudo cp /boot/grub/menu.lst /etc/Master_Copies
```

However that file is now gone in Karmic Koala.

Can someone give me the code to backup the now appropriate file(s)?

Would it be boot/grub/grub.cfg?

Thank you.

---

### Post by grandtoubab on 2009-10-31
not only, add:
**/etc/default/grub**

**/etc/grub.d/ (folder)**



[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Rytron on 2009-10-31
> **grandtoubab said:**
> not only, add:
**/etc/default/grub**

**/etc/grub.d/ (folder)**

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

So I should do something like this?
```

sudo cp /boot/grub/grub.cfg /boot/Master_Copies
sudo cp /etc/default/grub /etc/Master_Copies
sudo cp /etc/grub.d/ /etc/Master_Copies
```

---

### Post by ranch hand on 2009-10-31
That would probably be fine.  If you have a lot of OS' or want labels a custom file would be best and then that would be what you want to keep.

See link in sig for more info and links to a lot more info.

---

