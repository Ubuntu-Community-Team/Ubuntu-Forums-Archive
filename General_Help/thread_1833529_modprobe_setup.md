---
title: "modprobe setup"
date: 2011-08-26
forum: General Help
---

### Post by mixmaster on 2011-08-26
I have a motherboard problem which requires the forcedeth module be run with msi=0 and msix=0 (at least until I upgrade the mb bios).

I have created the file /etc/modprobe.d/forcedeth.conf containing the line

options forcedeth msi=0 msix=0

Now if, after booting, I do
```

sudo modprobe -r forcedeth
sudo modprobe forcedeth

```
everything works fine (ie my network connection starts).  However, I had expected the options to be picked up automatically at boot - I have had it working that way but had to reinstall.  Clearly I have forgotten a step. Can someone please jog my memory - do I need to put something in one of the init.d scripts or somewhere else?

Thanks

---

### Post by mixmaster on 2011-08-26
Well, after an update the system has started to find the options in forcedeth.conf as I expected it to in the first place.  I must admit I did not check all 150 or so updates so perhaps there was a bug fix.

Thanks anyway

---

