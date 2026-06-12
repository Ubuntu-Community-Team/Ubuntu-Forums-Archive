---
title: "Boot problem - &quot;Gave up waiting for root device.&quot;, (initramfs)"
date: 2010-05-25
forum: General Help
---

### Post by dd1linux on 2010-05-25
I am not sure what changes I made to have this happen, but anyway - I can boot into 2.6.31-14 kernel just fine, but when I try the more current 2.6.32-22 I get the "Gave up waiting for root device" error.  That kernel WAS working fine. I tried adding "rootdelay=200"  and changing the root=UUID=XXXXXXXXXXXXXXXX to root=/dev/sdh2 but neither worked.  I am looking at my grub.cfg file and there are no differences from one kernel to the next except for the obvious (the uuid is the same,etc.) Any help would be greatly appreciated.

---

