---
title: "not detecting flash drive."
date: 2011-04-09
forum: General Help
---

### Post by jewfromdahood on 2011-04-09
I know the flash drive works as my Xbox 360 will detect and use it... Ubuntu won't detect nor mount it.

---

### Post by chaozuper on 2011-04-09
this might be obvious, but have you run lsusb in the terminal with and without the flash drive plugged in? if the results are different, post the lsusb results from when the flash drive was plugged in.

---

### Post by HermanAB on 2011-04-09
Howdy,

Open a console, plug the schtick in, wait a few seconds and type:
$ dmesg

then report back here what you see and someone may be able to help you.

Chances are that all you need to do is fdisk and mkfs the thing.

---

