---
title: "Accessing File system from Windows Vista."
date: 2010-11-07
forum: General Help
---

### Post by Jetso on 2010-11-07
I have Ubuntu 10.10 and Windows Vista on my laptop. I would like to
be able to access the File System in Windows because I need to use iTunes to sync my iPod, while I actually get most of my Music in Ubuntu. Could someone tell me how I would go about doing this?

---

### Post by Morbius1 on 2010-11-07
You should have a listing of the Windows partition under Places. Click on it and it should mount it.

Unless you installed Ubuntu using Wubi in which case it's under /host.

---

### Post by Jetso on 2010-11-07
I'm sorry maybe I wasn't clear. I want to access Ubuntu file system FROM Windows, not the other way around. :)

---

### Post by Morbius1 on 2010-11-07
No, actually after reading your original post again you were very clear. I'm just a dingbat. There are some windows filesystem drivers that enable this sort of thing but I don't think they work with ext4. I don't use this sort of thing but I remember reading about them in the forum.

Sorry for the misunderstanding.

---

### Post by sikander3786 on 2010-11-07
Here is a workaround.

[http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

There are many guided on that. Just Google "ext4 windows".

---

### Post by Jetso on 2010-11-07
Hmmm... I saw something on here where someone use something called Samba? Is that a relatively easy method.

---

### Post by sikander3786 on 2010-11-08
Samba is intended for sharing files over the network. Is that what you want to do?

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html)

---

### Post by Sven6210 on 2010-11-16
I also have Ubuntu and Windows on a dual boot system. In order to have access to the data from both systems I have three partitions (not considering swap).

1. partition for Windows 7 and the installed applications (ntfs)
2. partition for ubuntu 10.04 and the installed applications (ext4)
3. partition for data (ntfs)

By having all data on a ntfs partition seperated I have two advantages:
- I can easily backup the data without backing up application or the OS itself
- I can access the data from Windows and Ubuntu without any workarounds

I guess Ubuntu would be performing better with data on an ext4 partition, however the two above mentioned advantages are more important for me. I am using this structure for a while and never faced problems

Only Thunderbird under Ubuntu has its data in the home directory in the ext4, where I can make separate updates - actually those updates are less important as I have an imap-account for emails and they anyway all remain on the server.

---

### Post by Mark Phelps on 2010-11-16
Please note that Ext2Read now claims that it can read Ext4 filesystems, which means, that it SHOULD be able to read 10.04 and 10.10 filesystems from inside MS Windows.

---

