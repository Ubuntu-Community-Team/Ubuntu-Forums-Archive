---
title: "How to automount a FAT32 drive on startup?"
date: 2010-05-23
forum: General Help
---

### Post by X-Windows on 2010-05-23
I've searched around on the forums but cant get this to work. Apparently I need to edit the /ect/fstab file and add a line to automount my FAT32 file on startup, but for some reason **gksudo gedit /ect/fstab** pulls a blank gedit document. I can read the doc by using the file browser,but cant edit permissions or write to it. I'm new to the Linux OS, so I'm probably not doing something obvious... I'm trying to get Ubuntu 10.04 to mount my FAT32 "Shared" partition on startup.

---

### Post by jerome1232 on 2010-05-23
It's not ect it's etc

```
gksu gedit **/etc/fstab**
```

You also might want to take a look at this
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by akakingess on 2010-05-23
Here is the [link]("https://help.ubuntu.com/community/MountingWindowsPartitions") for the official Ubuntu documentation on it as well, I highly recommend using the 'Ubuntu Help' link at the top of the forum page and you can search documentation/manuals for just about anything there. Good Luck!

BTW: You could also search there for setting up the sharing of the Fat32 partition, although you may also want to check and make sure that you have NTFS-3G installed within Ubuntu (it's in the repositories) IF you have trouble getting it to mount at all.

---

### Post by sharath.puranik on 2010-05-23
If you dont want to use fstab, go install the **ntfs-config** package.

Once **ntfs-config** is installed, go to **System > Administration  > NTFS Configuration Tool** to launch it and change the settings to your choice.

---

### Post by X-Windows on 2010-05-23
> **jerome1232 said:**
> It's not ect it's etc

...

[IMG]http://www.printedclothing.com/contents/media/pc429%20im%20with%20stupid.jpg[/IMG]


Thanks for the link, the pysdm Storage Device Manager is just what I needed. Thanks all!

---

### Post by kofm on 2010-06-15
Ntfs-3g only works with NTFS partitions. He has to mount a FAT32 partition :)

BTW pysdm works very well!

---

