---
title: "Kernel update in Jaunty not showing in bootloader"
date: 2009-12-05
forum: General Help
---

### Post by luigi_mb on 2009-12-05
1) Today's updates included linux-image-2.6.28-17-generic. Updater asked whether I wanted to keep the existing menu list, and absentmindedly I clicked Continue. /boot/grub/menu.list has no trace of the new kernel version, and I am not sure how to add it.

2) A second, related question has to do with the ATI (HD 3650) driver, which I had activate from Hardware Drivers ("ATI/AMD Proprietary FGLRX driver"). Assuming I can solve 1), what--if anything--should I do about the ATI driver?

Thank you for your help.

/luigi

---

### Post by ranch hand on 2009-12-05
As to your kernel problem, you need to run, in terminal;
```

sudo gedit /boot/grub/menu.lst

```
There are 2 entries for your last kernel, the normal and the recovery entries.

I would copy/paste both of them above where they are now and then edit those 2 entries to read your new kernel.  This will put that kernel at the top of your screen menu.

When you see that it works you can either remove the old kernel in synaptic or leave it there and "hash out" the 2 entries so they do not show up.  That is simply putting "## " before each line of the entry.  It will be there if you need to use it but it will not be on your screen menu at all.

---

### Post by luigi_mb on 2009-12-05
Thank you "ranch hand". Your suggestion worked! and I guess my second question got answered too, because on reboot everything is fine and dandy.

/luigi

---

### Post by ranch hand on 2009-12-05
Great, glad I could help.  In the short time I have been using Ubuntu, I have come to really love grub-legacy (what you are using).

Grub2 is a lot different, you have to do things in a very different way.  I think it is going to be even better.

I use an ATI card too so I am glad you are up and running with the bugger.

---

