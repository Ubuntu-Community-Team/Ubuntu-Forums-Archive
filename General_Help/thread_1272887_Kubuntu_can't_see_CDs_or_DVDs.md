---
title: "Kubuntu can't see CDs or DVDs"
date: 2009-09-22
forum: General Help
---

### Post by edd07 on 2009-09-22
Hello, I need some help.

Because of an update my DVD/CD drive stopped working in my Acer 4810TZ laptop. It's running Kubuntu Jaunty Jackalope. I'm guessing an update broke it because it used to work fine (burning too) but I tried to read some CDs today to find it didn't work anymore. 

When I insert a CD I'm no longer prompted, it doesn't show up in the Recently plugged in plasmoid or in Dolphin's sidebar. Not even the mount command seems to find it:
```

sudo mount /dev/cdrom /media/cdrom0
mount: /dev/sr0: unknown device

```*Is my code even right?*

I am completely sure it's not a hardware issue because it works fine in Windows.

I don't know if this is relevant, but it doesn't work even when the power-saving thingy is off (in Windows this mode turns off the CD drive)

I hope you'll be able to help me.

Thanks in advance.

---

### Post by edd07 on 2009-09-23
Bump.

---

### Post by edd07 on 2009-10-04
Bump again!

Can anyone help me?

---

### Post by StuartN on 2009-10-04
> **edd07 said:**
> Bump again! Can anyone help me?

Start with **sudo lshw -class disk** to check that the physical hardware is recognized. Assuming it is listed correctly, then get a data CD (like an Ubuntu installation disk if you have one handy) and insert it, then **mount**.

If the device is not listed then you probably have a hardware problem (disconnect, clean and reconnect) but if it is recognized but does not get mounted then try **dmesg | tail -30**.

Hopefully you will find something to report with those.

---

### Post by edd07 on 2009-10-04
> **StuartN said:**
> Start with **sudo lshw -class disk** to check that the physical hardware is recognized. Assuming it is listed correctly, then get a data CD (like an Ubuntu installation disk if you have one handy) and insert it, then **mount**.
Wow, thank you! That worked, it is listed correctly and I can then mount.

Will I have to run **sudo lshw -class disk** every time I want to mount a CD? Do you know why it's not mounted automatically?

Thanks again.

---

