---
title: "Running Ubuntu longside Windows 7"
date: 2012-02-04
forum: General Help
---

### Post by cmd.exe on 2012-02-04
Hey,
I've got 2 partions on my computer currently since this is for uni I've got a 2 partions running windows 7 ones for uni ones for just me :)
On the Ubuntu site it says you can run Ubuntu longside windows and thats what I want to do, does this mean I have to run ubuntu over a usb or use virtual box?

---

### Post by xyzzyman on 2012-02-05
If your university allows it, you're better off running on the short side or back side.

---

### Post by raja.genupula on 2012-02-05
no if you choose that option then it will install in your hard disk only and it will choose partition  automatically with out erasing any of your hard disk partition and with out information crashes . you can happily go with that option .

---

### Post by 3rdalbum on 2012-02-05
When the website says you can run Ubuntu alongside Windows, it's referring to installing it on your hard disk.

When you start the Ubuntu CD and run the installer, it shows an option called "Install Ubuntu side-by-side with Windows" or something similar to that. When you click on this option, you can select an existing partition to downsize, and how much you want to downsize it by.

The newly-freed space will be where Ubuntu creates its partition and installs itself to.

Alternatively, you can remove an existing Windows 7 partition and install Ubuntu to there. Or to a different hard disk. Or a USB flash drive. Or erase the whole hard disk and go with Ubuntu only. The installer gives you the options.

Just a warning though: Before running anything that can modify partitions (such as the Ubuntu installer) you MUST make a backup of all your important data. In rare cases you can lose data from resizing a partition, and it's better to be prepared.

---

### Post by xyzzyman on 2012-02-05
What you're most likely looking for is Wubi [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Be careful as it's max is 30GB's. That's more than enough for programs and your basic data, but for media you'll probably want to save and access from your NTFS windows partitions. I have actual installs of Ubuntu 11.10 and 12.04 but I still save my media and torrent's right to my NTFS partition so they are accessible from everywhere.

---

