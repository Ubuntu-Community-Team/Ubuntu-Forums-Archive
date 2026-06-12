---
title: "Before I get in too deep"
date: 2010-01-01
forum: General Help
---

### Post by Silvertones on 2010-01-01
I've got the bugs worked out. I love Ubuntu.
I still want to keep Windows XP for awhile until I'm satisfied I won't need it for something. I installed ubuntu "inside Windows" from the CD. Is this the best way to do it? Is Windows vulnerable this way? It's not running is it?
Last question:
If I decide I just want to have Ubuntu down the line do I have to start all over or is there a way to just get rid of Windows.
Thanks

---

### Post by atomizer on 2010-01-01
Personally I think it is not the best way to install Ubuntu in windows. You are limited by the loopback-device (with wubi you use a folder on your windows file system as a virtual partition, and there are limitations that way). You do not use the windows OS, just the folder, so there are almost no vunerabilities.

there are ways to migrate to a "real" partition.

see [here]("http://ubuntuforums.org/showthread.php?t=438591") for a guide.

---

### Post by SuperSonic4 on 2010-01-01
> **Silvertones said:**
> I've got the bugs worked out. I love Ubuntu.
I still want to keep Windows XP for awhile until I'm satisfied I won't need it for something. I installed ubuntu "inside Windows" from the CD. Is this the best way to do it? Is Windows vulnerable this way? It's not running is it?
Last question:
If I decide I just want to have Ubuntu down the line do I have to start all over or is there a way to just get rid of Windows.
Thanks

1. No, best is to shrink XP and give ubuntu it's own space

2. Pretty much yeah

---

### Post by Leppie on 2010-01-01
> **Silvertones said:**
> I installed ubuntu "inside Windows" from the CD. Is this the best way to do it? Is Windows vulnerable this way? It's not running is it?
Best way to install ubuntu with windows is side by side (i.e. ubuntu on it's on partitions). To some this may seem a complex operation, but in reality it's very easy with the ubuntu live/installation cd. Ubuntu isn't vulnerable to windows malware, however it doesn't make windows more vulnerable either. Instead, Ubuntu uses a highly reliable filesystem (ext4) which implemented within windows (using the highly unreliable ntfs) may cause issues. E.g. if windows doesn't shut down properly, Ubuntu cannot boot, or if windows is affected by viruses it may affect the Ubuntu installation as well.

> **Silvertones said:**
> Last question:
If I decide I just want to have Ubuntu down the line do I have to start all over or is there a way to just get rid of Windows.
it is a lot easier to get rid of windows when you have it side by side with ubuntu. the ubuntu system is now installed in a large file, serving as the ubuntu partition, within the ntfs partition. if you decide to switch to ubuntu only, you still have to do the repartitioning and basically re-install ubuntu to the new partitions.

---

### Post by Silvertones on 2010-01-01
Thanks for the answers. I think for the time being I'll leave it as is. When I decide I no longer need Windows on this machine I'll just do a complete reinstall of Ubuntu. This computer has a small drive. My music computer has to remain with Windows as my programs don't seem to want to run with Wine so I have that as a backup if I should need Windows for something Internet wise.

---

