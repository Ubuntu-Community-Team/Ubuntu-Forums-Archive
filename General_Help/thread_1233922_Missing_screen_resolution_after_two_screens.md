---
title: "Missing screen resolution after two screens"
date: 2009-08-07
forum: General Help
---

### Post by Snuzzer on 2009-08-07
Hi.

I had my television connected to my laptop which was running a resolution of 1200x800. After connecting my television I had to change the resolution to-- I think it was 1024x768.

I disconnected my television and restarted my laptop but after this the maximum resolution I can choose is 1280x720.

Is it possible to get the 1200x800 resolution back without reinstalling the whole system?

If it helps anything, my laptop is a [_Toshiba Sattelie Pro M70_]("http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=5190&part=4391#spectop").

Thanks in advance.
Simon B. Støvring

---

### Post by Snuzzer on 2009-08-09
Bump. No one knows?

---

### Post by Barafu Albino Cheetah on 2009-08-09
try sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Snuzzer on 2009-08-10
> **Barafu Albino Cheetah said:**
> try sudo dpkg-reconfigure -phigh xserver-xorg

It worked. Thanks! :)

---

### Post by zkriesse on 2009-08-10
in the systems/preferences/display there's options for just that kind of thing.

---

