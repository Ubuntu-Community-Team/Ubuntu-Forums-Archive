---
title: "format flash drive."
date: 2011-02-01
forum: General Help
---

### Post by christopherw on 2011-02-01
I am trying to format a flash drive as a GUID partition, using disk utility, (graphical and terminal) but I keep receiving the same error, I reboot and try again, I have googled the issue but I have not yet found a solution to my issue. is this a bug? or what can I do to resolve this.

Running Maveric...

((One or more partitions are busy on /dev/sdb)) wtf?

---

### Post by moody_mark on 2011-02-01
It looks to me like the USB device is still mounted. Open up a file browser window (Places --> Computer) you should see the USB device listed there, or on the left hand pane.

Right click the device and select unmount. Then go to the system --> administration menu and select "disc utility" you can then use this to format the USB stick.

---

### Post by FahadMKS on 2011-02-01
You may also select the Disk Utility from System >> Administartion, there you will have the option to unmount the drive and you can format as well as check the drive for errors.

Hope this was helpful.

---

### Post by christopherw on 2011-02-01
> **moody_mark said:**
> It looks to me like the USB device is still mounted. Open up a file browser window (Places --> Computer) you should see the USB device listed there, or on the left hand pane.

Right click the device and select unmount. Then go to the system --> administration menu and select "disc utility" you can then use this to format the USB stick.
thank you.

---

### Post by christopherw on 2011-02-01
I tried that, and got this error.

((Error creating partition table: helper exited with exit code 1: cannot open /dev/sdb: No medium found))

---

### Post by christopherw on 2011-02-01
Its resolved, thank you both. :) kudos

---

### Post by christopherw on 2011-02-01
Ok i did all that and the drive is formatted, but it is refusing to format it as GPT, even though that is the partition type i keep asking it to do, it formats it as Master Boot Record by default then show me this message...

((Error creating partition table: timeout (10s) waiting for change))

---

### Post by srs5694 on 2011-02-01
The timeout error suggests a hardware fault, or perhaps something is still using the disk.

Try these two commands just after you receive such a failure:

```

dmesg | tail
df -h

```

If you see references to "sdb" in the dmesg output, then those are kernel messages related to the device. Some may be normal (such as detection when you first insert the device), but if you see anything that sounds like an error message, it might provide more clues, so you might post it here.

If the "df -h" output includes any references to /dev/sdb or any partition on /dev/sdb, it means that the disk is still mounted. You should be able to unmount it with the "umount" command, as in "sudo umount /dev/sdb1" (or whatever partition is mounted).

You could also try another program. Most GPT-capable Linux partitioning tools are based on libparted, which does the real work, so I'd expect most of them to behave in the same way; but my [GPT fdisk (gdisk)]("http://www.rodsbooks.com/gdisk/") isn't based on libparted, so it might work, or at least produce a different error message. I recommend you download it from [its Sourceforge download page,]("http://sourceforge.net/projects/gptfdisk/files/") since the version provided in the Ubuntu repositories is hopelessly out of date. It's used much like fdisk, so you'd type "sudo gdisk /dev/sdb" to launch it, then type single-letter commands to manipulate the partitions (p to display, d to delete, n to create, etc. -- type "?" to see a command summary). Type "w" to save your changes. Be aware that GPT fdisk does *not* create filesystems in your partitions; you've got to use mkfs to do that.

---

