---
title: "change  root=/dev/sdb1 for grub2"
date: 2010-03-10
forum: General Help
---

### Post by monkeyking on 2010-03-10
I got the following line in my grub.cfg
```

linux   /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro   quiet splash

```
That I need to change to 

```

linux   /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro   quiet splash

```

How do I make this change, if I want the change to be persistent between system updates.

thanks

---

### Post by dcstar on 2010-03-11
> **monkeyking said:**
> I got the following line in my grub.cfg
```

linux   /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro   quiet splash

```
That I need to change to 

```

linux   /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro   quiet splash

```

How do I make this change, if I want the change to be persistent between system updates.

thanks

I believe the various Grub2 HOWTOs cover this sort of thing in detail, do a forum search for them.

---

### Post by monkeyking on 2010-04-13
> **dcstar said:**
> I believe the various Grub2 HOWTOs cover this sort of thing in detail, do a forum search for them.

This I did, feel free to point me to where in the HOWTO this is explained.

---

