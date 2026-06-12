---
title: "Live CD Suggestions Please"
date: 2010-02-17
forum: General Help
---

### Post by qaissi on 2010-02-17
I do a lot of work copying hard drives that use Windows. I normally pull the drives, hook them to Ubuntu with a USB connection and just use the File Manager to copy the drive's contents.

I don't want to compress the files or make an image I just want a direct copy.

This is usually done at my place but now I have to go elsewhere and do it.  So with an external USB hard drive in tow I was hoping to grab a SMALL Linux Live CD that had a GUI, a Disk Mounter, and a File Manager (not commander) and I could Boot off the CD and bypass all of the windows file restrictions on the computers I have to attach to.

Now I have downloaded a number of them: DSL, Deft, and Xubuntu only to find them too big or not user friendly enough for the simple tasks I need to do.

Any suggestions.

---

### Post by jamesisin on 2010-02-17
Just get the current 9.10 installation CD.  There is an option to try Ubu without making changes.  This is a Live CD.

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

You may have to learn a little about mounting drives, but that's easy enough:

[http://www.soundunreason.com/InkWell/](http://www.soundunreason.com/InkWell/)

Ubuntu also has an option to create a Live USB device (System &#8212;> Administration &#8212;> Create a USB startup disk).

That should get you started.

---

### Post by wilee-nilee on 2010-02-17
You can load a thumb as the previous post suggests also with netbootin. You can also use the live CD to boot then save the MS with a external drive or thumb.

---

### Post by t0p on 2010-02-17
As wilee-nilee tried to suggest, you can create a live USB stick with the program **unetbootin**.  I think it's in the repositories, so you should be able to install it with the terminal command

```
sudo apt-get install unetbootin
```Really, any Linux distro should be fine to do what you want.  If you just want to copy the contents of a hard disk, I'd suggest you use the program **dd** which will come in any Linux distro.  Read the manpage for details of its syntax; it's basically

```
dd if=/dev/the-disk-you-want-to-copy of=/path/to/where-you-want-to-copy-it-to.
```

There's a nice little guide to using dd to backup hard disks [here]("http://www.debianhelp.co.uk/ddcommand.htm").

---

