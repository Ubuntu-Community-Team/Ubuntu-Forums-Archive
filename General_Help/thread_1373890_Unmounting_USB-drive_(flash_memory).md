---
title: "Unmounting USB-drive (flash memory)"
date: 2010-01-06
forum: General Help
---

### Post by pingu1 on 2010-01-06
Hi !
I stupidly unplugget my USB-cable, which was connected to my Nokia music phone, just as if I were in Windows. What do I do? I've lost my music on the phone,
or, it seems it may be there (the correct mass of data), but my phone now tells
me there is no music...

Can I recover this? And - what is the correct way to unplug a USB unit in Ubuntu?
To make it work, and find the phone/drive - I just typed "sudo lsusb" in the terminal,
and it found and opened the memory automatically...

How should you unmount the USB, and maybe even how do I get my data back?

-Pingu1.

---

### Post by lotharmat on 2010-01-06
```
sudo umount [mounted thing] 
```

will unmount it!

---

### Post by pbrane on 2010-01-06
Normally when a device is mounted an icon shows up on the desktop. Right-clicking will bring up a context menu that will allow you to unmount the device cleanly. What happens is that some data may not have been written to the device when you unplugged it. If you have that music stored somewhere you should be able to write it back.

---

### Post by pingu1 on 2010-01-06
> **pbrane said:**
> Normally when a device is mounted an icon shows up on the desktop. Right-clicking will bring up a context menu that will allow you to unmount the device cleanly. What happens is that some data may not have been written to the device when you unplugged it. If you have that music stored somewhere you should be able to write it back.


What happened - it seems, is that my data has been converted (from what I can figure out) on the phone, to some format the phone does not read. 
It seems the data is there.. I hope.

What should I write after sudo umount ? 
Should I do a lsusb and write what I find to be the USBport or what?

Thanks.
-Pingu1:P

---

### Post by pingu1 on 2010-01-06
And I am hoping I can recover it by getting the music from the phone to be avaliable again, and not having to copy everything from my C:\drive over to the phone again.
I think I had some gigabytes of music...

Post scipturum - I think I have lost some other files as well. Like installfiles and other
updatefiles on the phone software. Do you lose your files if unplugging?
I was _NOT_ copying anything to the phone at the time I unplugged it...

---

### Post by pingu1 on 2010-01-06
anyone?

---

### Post by pingu1 on 2010-01-07
Ok. I formatted the entire disk, because I was running Ubuntu while still having Windows. Now everything works. I will now unmount everything before removing them...!!!

Thanx.

---

### Post by audiomick on 2010-01-07
On mine, the mounted device shows up in Nautilus with a symbol that looks like the eject button on a CD player next to it. If you click on this, it unmounts cleanly, or tells you the device is still busy.

---

