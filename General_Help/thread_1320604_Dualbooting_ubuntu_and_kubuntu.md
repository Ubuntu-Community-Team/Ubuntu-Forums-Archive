---
title: "Dualbooting ubuntu and kubuntu"
date: 2009-11-09
forum: General Help
---

### Post by Romanrp on 2009-11-09
I have installed ubuntu first.
A few weeks later I partition my hdd and installed kubuntu.
If I remove the kubutnu partition,will that cause any effects?
I did the same thing but it was vista,not ubuntu and I got Grub error 22.
is there a way I can avoid grub error 22?

---

### Post by Giblet5 on 2009-11-09
Before you blow kubuntu away, boot into Ubuntu and remove the Kubuntu boot option (if you have one), then re-write the grub MBR via
```
sudo update-grub
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

Now you can blow kubuntu away safely.

---

### Post by Romanrp on 2009-11-09
Did that ^^.
Then I deleted kubuntu
But the kubuntu swap partition remained.
And when I right click on the ubuntu partition it won't let me resize it.
I am using gparted on ubuntu-not the live cd.
I'l try it using the live cd.

---

