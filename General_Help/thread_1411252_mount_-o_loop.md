---
title: "mount -o loop"
date: 2010-02-19
forum: General Help
---

### Post by kaj on 2010-02-19
I need to flash my BIOS to get rid of an error: "Intel uCode loading error".

On [http://www.linuxinsight.com](http://www.linuxinsight.com) I have found a tutorial, that looks to be fine. I can even see in the comments, that somebody have done this with success from Ubuntu 9.04, the very same system, that I use.

Nevertheless I cannot make this bootCD with my Ubuntu 9.04, as it doesn't know the loop option to mount the image.

In the tutorial it says: "Requirements for this step is that you have support for the vfat and loop file systems in the kernel. Or you can have those features compiled as modules. In the latter case you can load the modules before the next step, like this:
modprobe vfat
modprobe loop
"
loop doesn't seem to be present in my system, and the command modprobe loop returns an error that the module is not available.

I tried to follow the tutorial anyway, but with no success.

How can I get the module lopp? I also want to use it to make iso images bootsble from the harddisk.

Kaj Rasmussen
Denmark

---

### Post by oshunluvr on 2010-02-19
Please post the actual command you are entering and the error output.

How are you planning to make an iso bootable from the hard drive by mounting it???

You can access it - but I'm rather sure you can't boot an .iso. You might be able to create a bootable partition from an iso, but it's a lot of work.

---

### Post by kaj on 2010-02-20
My ASUS Pundit PH3 has no floppy drive, in fact, it has no floppy controller at all. To flash the BIOS I had to make a bootable CD with the flashing utility. I found this tutorial:

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

It didn't work in my Ubuntu. But I have solved the problem now, and I have successfully flashed the BIOS.

There were no problems running the tutorial in PCLinuxOS 2009 Gnome edition.

---

