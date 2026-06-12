---
title: "&quot;Device not ready&quot; ralink rt73usb (rt2501) 9.10 wireless"
date: 2009-11-11
forum: General Help
---

### Post by robinPain on 2009-11-11
Thanks to "krogulec" here:-

[http://ubuntuforums.org/showthread.php?p=8244101]("http://ubuntuforums.org/showthread.php?p=8244101")

I can now start (required every powerup) my wireless link with
```
rfkill unblock all
```

prior to that "lshw -C network" reported wlan0 as "DISABLED" after upgrading to 9.10

On 9.04 both the inbuilt ralink rt2501usb and an external Netgear rtl8178 wireless hardware worked out-of-the-box.

After upgrading both failed to work; clicking the wireless icon showed both devices as "device not ready"

Doing an lsmod showed that both modules, rt73usb and rtl8187 were loading OK (I have 9.04 on the other half of this hard drive and so can compare both listings of lsmod - they are the same in this respect).

It seems that there is some elementary thing in the "network manager" i.e. right-clicking the wireless icon, such as, the little box marked "Enable wireless" is simply not overcoming the block on wireless enabled.

---

