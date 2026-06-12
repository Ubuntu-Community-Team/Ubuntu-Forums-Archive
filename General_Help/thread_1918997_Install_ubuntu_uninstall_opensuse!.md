---
title: "Install ubuntu uninstall opensuse!"
date: 2012-02-02
forum: General Help
---

### Post by vandermonde on 2012-02-02
Hi, I already have opensuse 12.1 installed to my computer along side with windows 7.
I want to replace opensuse with ubuntu . is there any body knows how can I do it.

---

### Post by deathadder on 2012-02-02
Hi,

First off make sure you backup anything on your SuSE install that you want to keep. Then you can simply write the Ubuntu image to disc or USB stick and boot off it and start the install. During the installation it'll ask you about how to partition your machine. The default is either guided or automatic (I can't remember the exact wording) but you want to choose "Manual partitioning".

Then you'll be able to either delete your SuSE partitions and get Ubuntu to automatically use the free space, or choose the individual partitions and set the mount points for them. You'll want to make sure you that you format the partitions if you are just setting the mount point to make sure that none of the permissions etc from SuSE get carried over.

---

### Post by vandermonde on 2012-02-02
> **deathadder said:**
> 

First off make sure you backup anything on your SuSE install that you want to keep. Then you can simply write the Ubuntu image to disc or USB stick and boot off it and start the install. During the installation it'll ask you about how to partition your machine. The default is either guided or automatic (I can't remember the exact wording) but you want to choose "Manual partitioning".

Then you'll be able to either delete your SuSE partitions and get Ubuntu to automatically use the free space, or choose the individual partitions and set the mount points for them. You'll want to make sure you that you format the partitions if you are just setting the mount point to make sure that none of the permissions etc from SuSE get carried over.

Thank you I'll do it. I hope it doesn't crash my windows boot .

---

### Post by deathadder on 2012-02-02
It shouldn't cause any problems; Windows will be added to the grub menu so you'll still be able to get into it. As with all things though there is the possibility that you may run into problems. So all I can suggest is backup your data.

That being said, the only problem I ever had when installing Linux alongside Windows what when I resized a Windows partition without defragging / cleaning up the Windows install...and that was years ago now. On the machines I do dual boot, I haven't had any problems in the time I've been using Ubuntu.

---

### Post by vandermonde on 2012-02-02
Thank you, solved.
:D

---

