---
title: "Ext3 partition mounts as root (gnome-volume-manager missing)"
date: 2009-07-08
forum: General Help
---

### Post by FoH on 2009-07-08
A while ago I re-partitioned my USB pendrive with an ext3 partition, amongst others. I discovered that this partition got mounted with root privileges, when I was about to copy some files to it. I didn't reflect on it then, I just sudo a cp command from a terminal instead, figuring the problem would fix it self at another mount or something. Ofcourse, it didn't :D

So I went at the problem again this evening. So I first tried setting some extra mount options on the drive and volume within Nautilus (and Gconf too). Whatever I entered I got "Couldn't mount. Wrong options" type of message. So I googled a bit and read about gnome-volume-manager, which I tried finding on my system. I turns out I don't have it! I'm guessing this is the cause of the error messages.

I'm guessing this package should be installed by default, right? That means I must have uninstalled it at some point. And I can understand why by the dependencies it has. I'm apparently forced to have Totem with all it's plugins just to have gnome-volume-manager. Is there a way around this? I can't imagine gnome-volume-manager really depending on those things to function.

Help for either being able to automatically mount ext3 systems with user privileges, or having gnome-volume-manager installed without the other packages would be much appreciated :)

I'd rather not resort to using fstab, I want the dynamic handling that Gnome should be able to offer. Also, it's worth mentioning that fat32 partitions mounts as they should, probably due to the settings in Gconf about the vfat type.

(Using Jaunty x64)

---

### Post by FoH on 2009-07-17
Well, I might as well provide an update to this issue. I was able to install the gnome-volume-manager without the recommended dependencies (which apparently was the problem) by apt-get:ing it from a terminal.

That didn't fix the problem though. I don't even think gnome-volume-manager is used in this case. Seems to have been replaced by gnome-mount and something else...

Passing options to the volume manager doesn't work at all, and finding help on this seems impossible. I've been reading about gnome-mount a little, and tried mounting from a terminal. Nothing works. It seems that the issue is that ext3 doesn't have an entry in gconf (under System -> Storage -> default_options) , and I can't figure out how to add this.

I find it incredibly strange that ext3 doesn't work "out of the box". Seems like a basic thing. Googling on the issue finds a bunch of people who have had problem with ext3 partitions and permissions, many posts are several years old. It seems that a possible solution is adding a fixed mount point, which might be what I have to do... Not a good solution, the partitions might change and I rather not make a "hard link" between a specific partition and a mount point because of this.

---

