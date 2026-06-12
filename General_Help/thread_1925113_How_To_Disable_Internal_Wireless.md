---
title: "How To Disable Internal Wireless"
date: 2012-02-14
forum: General Help
---

### Post by TheKismet on 2012-02-14
I am trying to disable internal wireless card on my Dell Inspirion N5110. I can't turn it off in bios. I want to use a usb external wireless instead. Thanks for the replies in advance.

---

### Post by wildmanne39 on 2012-02-14
Hi, post the output of:
```
lspci -nnk | grep -iA2 net
```
```
lsmod
```
so I can tell you how to blacklist the driver for your card.
Thanks

---

