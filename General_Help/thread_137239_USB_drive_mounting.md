---
title: "USB drive mounting"
date: 2006-02-27
forum: General Help
---

### Post by cbudden on 2006-02-27
Hello.  I have a Creative Zen, and a problem with disk mode automounting.

If I set the capacity to below 4GB, it automounts fine.  Anything above - big no no, doesn't mount.  Now it used to work a while back (at 8 GB), but I believe there have been problems with automount usb with Ubuntu.  I can manually mount it using 
```

sudo mount -t vfat /dev/sda /media/manmount

```

And it works, I can access the contents fine. 

It automounts in Windows XP above 4GB.

What do you think is going on?

Chris

---

### Post by Stinger on 2006-02-27
[QUOTE=cbudden] I believe there have been problems with automount usb with Ubuntu. 

What do you think is going on?

Chris[/QUOTE]

I can confirm the automount problems , a system upgrade Using the upgrade tool solved the problem for me.
But then again my usb harddrive is using rieserfs.
:-k

---

### Post by cbudden on 2006-02-27
Do you mean sudo apt-get update && upgrade ?

---

