---
title: "Accessing data after Pogoplug"
date: 2010-04-20
forum: General Help
---

### Post by JonathanT on 2010-04-20
I have installed a Pogoplug. I am trying to get it to mount but I do not know what to put in the line after /dev/. If I am even using the correct code.

sudo mount -t ntfs-3g /dev/sdb1 /media/pogoplug

I was trying to use the information from the how to mount a USB from

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)


I have the pogoplug installed and can get the help information through the commandline. The folder /media/pogoplug has also been created.

---

### Post by beren.olvar on 2010-04-20
when you plug an usb device, normally the output of "dmesg" will tell you what entry in /dev/ it is using.

look for something like this:
```

olvar:~$ dmesg
...
sd 4:0:0:0: [sdb] Assuming drive cache: write through
 sdb: sdb1
sd 4:0:0:0: [sdb] Assuming drive cache: write through
sd 4:0:0:0: [sdb] Attached SCSI disk
...

```

in my case the device (a standard usb disk, not a pogoplug) is now on /dev/sdb1
maybe in [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html) you can find how to automount your device.

---

### Post by JonathanT on 2010-04-21
That doesn't work because Pogoplug is not connected to the computer directly. I think that is my problem. It is connected through the internet. I have a Drobo connected to the Pogoplug which is connected to my router. I can access my data by going to the Pogoplug website or by using Pogoplug software. It works on my XP box, but I can not figure out how to get it to work on my Ubuntu box.

---

### Post by beren.olvar on 2010-04-21
If you are accessing it through the internet, it is not going to be shown on /dev/
Have you tried this? [http://www.pogoplugged.com/category/37/Pogoplug-Drive-for-Linux](http://www.pogoplugged.com/category/37/Pogoplug-Drive-for-Linux)

I don't know the specific characteristics of the Pogoplug, but if it has a built in ssh server, you can also try mounting it with sshfs+FUSE
(look here for instructions [http://myy.helia.fi/~karte/mount_sshfs.html](http://myy.helia.fi/~karte/mount_sshfs.html))

or within nautilus go to Places-> Connect to Server
and enter the required information.

If you are trying to reach it from outside your lan, probably you will also need to configure you router to allow the access.

---

### Post by JonathanT on 2010-04-24
Thanks for the web listing beren. It is working like a dream now. 

Thanks for you information.:)

---

