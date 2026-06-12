---
title: "Virtual Box OSE &amp; WIndows"
date: 2010-09-26
forum: General Help
---

### Post by ericstrom on 2010-09-26
Running Ubuntu 10.04 Lucid Lynx. Everything is currently on a 40 GB IDE drive (sda) that's getting full with data files. Only a few GB left. I have a second 40 GB IDE drive (sdb)that's empty. Currently set up as Ext 4. Doesn't mount automatically.

I would like to be able to run Windows XP and a few Windows programs on occasion that wont run under Wine. I already have Virtual Box OSE installed on sda and I was thinking that would be the way to go. But with no room left on sda, I need to do something else. Also, I've never used Virtual Box OSE.

Wondering what the best way to set things up is ? Do I set up the second drive (sdb) as root or non root file system ? Do I set the second drive up as NTFS-3G ? ANy suggestions would be GREATLY appreciated. Pretty much a novice in all this including how to get the second drive to mount automatically.

---

### Post by Merk42 on 2010-09-26
Just install Virtualbox (you may want to get the PUEL version which has more features)

In either event once Virtualbox is installed, go to File > Preferences.  From there in General tell it to have the Default Hard Disk Folder and Default Machine Folder be on sdb.

After you do that, just make sure you mount sdb before running Virtualbox.

---

### Post by ajgreeny on 2010-09-26
I think the best way for you to do what you want is to format the new drive as ext4, mount it at boot time by making the folder /media/data ```
sudo mkdir /media/data
``` and doing a simple edit of /etc/fstab by adding the line 
```
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /media/data ext4 defaults,relatime 0 2
```Note that your UUID will be different from mine shown here and you can get yours for the sdb partition with the command ```
sudo blkid
```Now you can copy some of your data files from your current home folder to sdb and use them quite easily.  You will also need to delete the files from your current home folder as they will only copy, not move, when using nautilus to drag/drop to another partition.

EDIT:

You could try what Merk42 said, but I was assuming you did not have available space to install a windows virtual machine at the moment.

I still believe that using sdb as a data partition is the answer, but try both ways and see which you prefer.

---

