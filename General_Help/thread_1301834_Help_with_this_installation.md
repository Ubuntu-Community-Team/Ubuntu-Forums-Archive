---
title: "Help with this installation"
date: 2009-10-26
forum: General Help
---

### Post by sabrecool on 2009-10-26
I need to install this driver for my desktop

[http://www.asix.com.tw/FrootAttach/driver/AX88772_772A_178_LINUX2.6.9_REV122.zip]("http://www.asix.com.tw/FrootAttach/driver/AX88772_772A_178_LINUX2.6.9_REV122.zip")

but I don't know how. I tried the 'make' command but it doesn't compile. There are 2 drivers for linux and I picked the driver above form here

[http://www.asix.com.tw/products.php?op=pItemdetail&PItemID=86;71;101&PLine=71]("http://www.asix.com.tw/products.php?op=pItemdetail&PItemID=86;71;101&PLine=71")

I am a total newbie with Linux so please provide me with every single command.

---

### Post by vidak on 2009-10-26
Are you sure you need to compile the driver? Probably it would be enough to change the configuration, if the device doesn't work.
Try:
```
tail -f /var/log/messages
```
and plug/unplug the device to see what happens - is it recognized?

---

