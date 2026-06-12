---
title: "What is LTS (as in 10.04 LTS)?"
date: 2012-01-08
forum: General Help
---

### Post by noloader on 2012-01-08
Hi All,

I bought an Asus Transformer (TF101). Its an Android tablet running 3.2 (Honeycomb). I've been trying to use it with Ubuntu 10.04 x64 (my platform of choice to avoid Unity).

The tablet is not recognized since it is an MTP device. I tried following [1] and [2], but all I get is "Transport endpoint is not connected" when trying to cd into /media/transformer. Under file manager (double click the drive icon on the desktop), and I get "Could not open the file /media/transformer" from gedit.

What precisely is supported long term in Ubuntu 10.04 LTS? mtpfs appears broken, so it can't mount MTP devices. In addition, the Android plugin for Eclipse will not run due to Eclipse being down level (3.6.2 is required, 3.5 is provided, so I can't install required tools)?

Jeff

[1] [http://www.pclinuxos.com/forum/index.php?topic=100896.0](http://www.pclinuxos.com/forum/index.php?topic=100896.0)
[2] [http://forum.xda-developers.com/archive/index.php/t-1077572.html](http://forum.xda-developers.com/archive/index.php/t-1077572.html)

---

### Post by Paqman on 2012-01-08
> **noloader said:**
> What precisely is supported long term in Ubuntu 10.04 LTS?

The whole system receives longer support for both hardware and software updates. To get the latest stuff you would need to enable backports in Software Sources, but that won't help for mtpfs.

> 
mtpfs appears broken, so it can't mount MTP devices.


Other folks seem to report being able to mount Android 3.2 devices. I suspect the problem isn't mtpfs itself, becasue the version in later versions of Ubuntu is the same, but some of the dependencies like libmtp have been updated.

See if you can connect to the device with a LiveCD or USB of Oneiric. If you can then you'll want to look at getting the Oneiric packages into Lucid. You can do that by manually downloading the required packages from packages.ubuntu.com, but you'd have to make sure you satisfied all the dependencies yourself, which could be a bit of a pain.

> 
In addition, the Android plugin for Eclipse will not run due to Eclipse being down level (3.6.2 is required, 3.5 is provided)?


Again, you're hampered here by choosing to use an older version of Ubuntu. There doesn't seem to be a PPA for Lucid. So again, you're looking at either installing manually or switching to a newer version of Ubuntu (which you can do without using Unity).

---

### Post by C.S.Cameron on 2012-01-08
The locked bootloader will be fixed Jan 12th, see:


[http://www.afterdawn.com/news/article.cfm/2012/01/03/transformer_prime_getting_android_4_0_on_january_12th_along_with_unlocked_bootloader](http://www.afterdawn.com/news/article.cfm/2012/01/03/transformer_prime_getting_android_4_0_on_january_12th_along_with_unlocked_bootloader)

---

