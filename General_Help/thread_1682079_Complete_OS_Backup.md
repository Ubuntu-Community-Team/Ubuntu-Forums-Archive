---
title: "Complete OS Backup"
date: 2011-02-05
forum: General Help
---

### Post by gurudev1000 on 2011-02-05
Hi,
Can you please tell me reliable and updated way of backing up ubuntu installation in such a way that I can use the backup 'image' to boot into later if the original installation gets faulty? I am using an HDD which might crash anytime. And I can't afford to install Ubuntu in a new partition all over again and download the huge amount of updates that I had doing in Linux.

Perhaps I can also ask for help in moving or copying the installation into another partition in such a way that the copy also works like a proper install?

please give useful links as well..

---

### Post by Frogs Hair on 2011-02-05
Take a look at this. [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by tea for one on 2011-02-05
Yes, I agree, Remastersys is a good program, pretty easy to use and it will allow you to include personal data if you wish.

You can also use the Ubuntu Startup Disk Creator to put your remastered iso on a USB stick in order to install on a new HDD.

---

### Post by gurudev1000 on 2011-02-06
> **Frogs Hair said:**
> Take a look at this. [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Thanks for mentioning this software. Seems like a good one.
I installed it and  using the GUI (instead of command line) selected the 'BACKUP COMPLETE SYSTEM INCLUDING USER DATA'. It has created 2GB ISO in */home/remastersys/remastersys* folder. I tried using *UnetBootin* to write this ISO into my pendrive and it doesn't work on Bootup the way a regular Ubuntu ISO works. Also.. I have atleast used 5 GB of my Ubuntu partition (installed softwares and such). Not sure why this is only 2GB of ISO backup.

So... what's the thing I missed?

---

### Post by Rubi1200 on 2011-02-06
Clonezilla is another option worth considering:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by tea for one on 2011-02-06
> **gurudev1000 said:**
>  I tried using *UnetBootin* to write this ISO into my pendrive and it doesn't work on Bootup the way a regular Ubuntu ISO works. Also.. I have atleast used 5 GB of my Ubuntu partition (installed softwares and such). Not sure why this is only 2GB of ISO backup.

So... what's the thing I missed?

Good evening

I suggest that you try the following:-

(a) Use Remastersys to create another Customiso without personal files
(b) To install on a USB pendrive, try your old and new iso files using
    System > Administration > Startup Disk Creator

Please let us know if there was any success?

---

### Post by gurudev1000 on 2011-02-12
> **tea for one said:**
> Good evening

I suggest that you try the following:-

(a) Use Remastersys to create another Customiso without personal files
(b) To install on a USB pendrive, try your old and new iso files using
    System > Administration > Startup Disk Creator

Please let us know if there was any success?

Actually, I gave up by the time you replied and have installed a clean Ubuntu with a separate /home partition. Hope I won't have to go through this sh*t again.

I really appreciate your reply. Thanks

---

### Post by tea for one on 2011-02-12
To be honest, the Ubuntu installation is pretty quick in the event of a catastrophe especially if you have a separate /home partition.

Also, if you have a quick broadband, it's pretty easy to re-install your favourite packages.

Remastersys comes into own if you do not want to find and install all your software, themes etc.

---

