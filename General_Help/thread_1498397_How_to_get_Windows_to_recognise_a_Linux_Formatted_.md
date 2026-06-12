---
title: "How to get Windows to recognise a Linux Formatted Hard drive?"
date: 2010-05-31
forum: General Help
---

### Post by silkworm2.5 on 2010-05-31
Hi
Is there any way to make windows recognise my second hard drive (Which is fully exclusive to ubuntu) and access it? Iv'e been getting a few BSOD's since installing ubuntu and I'm pretty sure it's because windows keeps trying to access it and failing.

---

### Post by TheDesertDragon on 2010-05-31
I'm afraid not.

However, you can mount Ext3, and since the Ext filesystem is backwards compatible, you can mount an Ext4 as an Ext3 and that way basically interact with your Linux parition from Windows.

[http://ubuntuextreme.blogspot.com/2009/01/how-to-mount-ext3-filesystem-in-windows.html](http://ubuntuextreme.blogspot.com/2009/01/how-to-mount-ext3-filesystem-in-windows.html)

EDIT:
Also, Windows won't crash when attempting to access devices it cannot find the proper driver for. (Such as an Ext filesystem) It just won't load it. At most you'll notice a small performance loss every now and then, but since nearly all computers have at least one unrecognized device it really doesn't matter.

There's plenty of good reasons why you should be able to access your Linux partition under Windows, just like you can do the opposite, but avoiding BSOD's isn't one of them. (My Win7 never BSOD's)

---

### Post by lmarmisa on 2010-05-31
Windows does not recognize the Linux volumes (ext2, ext3, ext4).

There are some programs that can help you:

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

