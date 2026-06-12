---
title: "USB Key not recognised"
date: 2010-09-06
forum: General Help
---

### Post by necrosmash on 2010-09-06
Hi, there. I'm a long time lurker here, but haven't posted before.. Glad to be here, and hopefully someone will be able to help out with my problem.

I have a problem with a USB pen drive not showing up when inserted. It shows up fine in Windows XP, but nothing happens when I plug it into my laptop (I'm running Mint 9).

When I run lsusb in a shell, the USB key in question shows up as this:

```
Bus 002 Device 035: ID 1e3d:2088
```Anyone have any ideas on where I should go from here?

---

### Post by krimzonstarr on 2010-09-06
If you can specify the type of usb thumbdrive that may be helpful.
When you insert the usb drive, what exactly doesn't come up?

Does ```
ls /media/
``` show the drive?

---

### Post by necrosmash on 2010-09-06
Hi, I meant that the icon that would normally appear on my desktop to give me access to the USB key's contents through nautilus doesn't appear. I can't find it anywhere in nautilus.

The key doesn't show up in /media, either. As for the brand, I'm sorry but I have no idea what brand it is. All I know is that I have 2 of these 4GB sticks and neither of them are getting recognized.

---

