---
title: "command line USB"
date: 2009-12-15
forum: General Help
---

### Post by complete n00b on 2009-12-15
Something weird has happened to my video card and I can't use the GUI. I need to get my files off so I can reinstall the operating system.

Please tell me how to use the command line to copy files on to a USB. I don't even know how to find the USB using the command line. As my name suggests, I don't know anything.

---

### Post by complete n00b on 2009-12-15
I need to clarify...

the only command line I can get into is the grub command line. If I try to load up ubuntu normally I just wind up frozen on white and black parallel lines.

---

### Post by howefield on 2009-12-15
> **complete n00b said:**
> I need to clarify...

the only command line I can get into is the grub command line. If I try to load up ubuntu normally I just wind up frozen on white and black parallel lines.

Not sure what you mean by grub command line, have you been able to log in into your system. If you have...

At the command line, try typing the following to find your usb disk.

```
cd /media
```
```
ls
```

cd means change directory and ls lists the files in that directory.

Do you recognise your disk ? Mine is labelled "Backup" so for me to copy my /home folder to it would mean typing

```
cp -R /home/* /media/Backup/
```

---

### Post by 3rdalbum on 2009-12-15
The GRUB command line does not have the ability to do this. Try booting up from a live CD and copying that way.

---

### Post by complete n00b on 2009-12-15
there's something very wrong with my computer, I don't know what's going on, but when I try to boot from a liveCD I get the same problem. Is there a way I can somehow get from grub into a command line? I am desperate.

---

### Post by 3rdalbum on 2009-12-15
> **complete n00b said:**
> there's something very wrong with my computer, I don't know what's going on, but when I try to boot from a liveCD I get the same problem. Is there a way I can somehow get from grub into a command line? I am desperate.

Maybe your graphics card has died.

Can you edit the kernel line in GRUB? I gather you can start booting Ubuntu from GRUB? If you can modify the kernel line, then you should edit the bit that says "init=/bin/init" to read "init=/bin/sh". This loads up the kernel and basic userspace, but nothing else.

Then you can attempt to find out the device file name of your USB disk by typing:

```
fdisk -l
```

Let's say for instance that it shows that your USB device is /dev/sdf.

Next you need to create a mount point for the USB device:

```
mkdir /media/recovery
```

And mount it:

```
mount /dev/sdf /media/recovery
```

Now change into your home directory: (assuming that 'username' is your user name)

```
cd /home/username
```

Are you okay from here with copying files? If you get stuck, take a look at [www.linuxcommand.org;](www.linuxcommand.org;) it should have some details about how to copy files from one place to another.

After you're done, run this command:

```
umount /media/recovery
```

You might see the computer pause to think for a while. When it's stopped thinking and you've got the regular prompt back again, it's safe to remove the USB disk. Now you can shut down:

```
halt
```

---

### Post by complete n00b on 2009-12-15
okay I can get to the command line from grub easy enough, but I cannot locate my usb drive. is it normally in the /media or the /dev directory?

---

### Post by northern lights on 2009-12-15
While the device will appear under /dev - file access is done either via /media or /mnt

---

### Post by complete n00b on 2009-12-15
ignore that last question... :)

---

