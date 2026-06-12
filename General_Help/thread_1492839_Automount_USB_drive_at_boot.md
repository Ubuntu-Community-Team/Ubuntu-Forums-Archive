---
title: "Automount USB drive at boot"
date: 2010-05-25
forum: General Help
---

### Post by Lhademmor on 2010-05-25
Hi all. I have an external USB harddrive connected to my PC, as it contains all of my music among other things. However, when I boot Ubuntu and go into my media player, I can't play the songs in my library as the drive has to be manually mounted every time I start-up.

Is there any way to have Ubuntu auto-mount it at boot, like Windows does? I'm aware that the whole mount thing is there for security purposes, but in this case I just want it mounted and ready to go when I boot.

---

### Post by garvinrick4 on 2010-05-25
> **Lhademmor said:**
> Hi all. I have an external USB harddrive connected to my PC, as it contains all of my music among other things. However, when I boot Ubuntu and go into my media player, I can't play the songs in my library as the drive has to be manually mounted every time I start-up.

Is there any way to have Ubuntu auto-mount it at boot, like Windows does? I'm aware that the whole mount thing is there for security purposes, but in this case I just want it mounted and ready to go when I boot.
Go to configuration editor if it is installed will be in Applications to System tools. If not
hit Alt and F2 and then type in gconf-editor and click run. Go to apps in configuration editor
to nautilus to preferences and check the box media automount and if you want it to open everytime click that box also.

---

### Post by Lhademmor on 2010-05-26
> **garvinrick4 said:**
> Go to configuration editor if it is installed will be in Applications to System tools. If not
hit Alt and F2 and then type in gconf-editor and click run. Go to apps in configuration editor
to nautilus to preferences and check the box media automount and if you want it to open everytime click that box also.

I tried that. The strange thing is, both of the boxes are already checked!

---

### Post by dino99 on 2010-05-26
goto synaptic and reinstall pmount and usbmount

mountmanager is a nice tool to manage your partitions and devices

---

### Post by Lhademmor on 2010-05-29
> **dino99 said:**
> goto synaptic and reinstall pmount and usbmount

mountmanager is a nice tool to manage your partitions and devices

I tried all of it, but it still doesn't seem to work as it should. Also Mountmanager is useless: I select the external HDD and set its mount point as /mnt/Elements and click apply (as sudo), but the next time if I restart it, it seems to have forgotten what I just wrote. :mad:

---

### Post by MaX on 2010-09-08
by the "/mnt/Elements" line I guess you have a Western Digital Elements HDD?

I have one too, and each time I boot up Linux it says that it has trouble mounting it, I can S(kip) or fix it M(anually).

If I do a manual fix
I can mount it with ntfsmount /dev/sdd1 /media/Elements and it will work
until I reboot again.

But even though I have everything set in the fstab it won't mount automatically, ever!

My Western Digital My Book (Essential Edition 2.0) works fine in Ubuntu.

---

### Post by quirkification on 2010-09-08
My class is about to start so I cannot get working on this yet, to have my two partitions automount.

But I was wondering, How come a wallpaper from my partition will be displayed but none of the information is viewable until I mount the drive? Is this just because the image was previously reloaded? just curious.

---

### Post by MaX on 2010-09-09
> **quirkification said:**
> My class is about to start so I cannot get working on this yet, to have my two partitions automount.

But I was wondering, How come a wallpaper from my partition will be displayed but none of the information is viewable until I mount the drive? Is this just because the image was previously reloaded? just curious.

The wallpaper is probably in /var/tmp or something.

---

