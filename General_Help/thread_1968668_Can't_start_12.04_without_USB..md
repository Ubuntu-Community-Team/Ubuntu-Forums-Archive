---
title: "Can't start 12.04 without USB."
date: 2012-04-29
forum: General Help
---

### Post by &lt;bogisha/&gt; on 2012-04-29
I installed Ubuntu 12.04 from USB stick today, but it seems that my grub menu is installed on USB, so I can't start my pc without USB stick. I already tried to google for solution but nothing works for me.

I tried Yannbuntu's boot repair and tried installing grub on sda from terminal and nothing works. I will appreciate any help. Thanks.

---

### Post by C.S.Cameron on 2012-04-29
> **<bogisha/> said:**
> I installed Ubuntu 12.04 from USB stick today, but it seems that my grub menu is installed on USB, so I can't start my pc without USB stick. I already tried to google for solution but nothing works for me.

I tried Yannbuntu's boot repair and tried installing grub on sda from terminal and nothing works. I will appreciate any help. Thanks.

Try booting with the USB, then do an 
```
update-grub
```

---

