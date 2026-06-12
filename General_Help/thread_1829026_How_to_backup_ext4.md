---
title: "How to backup ext4 ?"
date: 2011-08-20
forum: General Help
---

### Post by fjkum on 2011-08-20
Hi,

I have installed Ubuntu 11.04 onto HP EliteBook 8540w notebook and would like to backup the entire disk using some popular backup tool.

I have searched in the internet and found the closest tool is PartImage. But the bad news is that it does not support ext4 fs!

So anyone out there can recommend other tools?

---

### Post by LowSky on 2011-08-20
clonezilla should work for you.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by sahabcse on 2011-08-20
Try to use the "dd" command.

---

### Post by walt.smith1960 on 2011-08-20
I use a commercial alternative, Image for linux.  I'm in no way associated with the vendor except as a customer but the program has saved my butt.  I use their boot manager as well.

[http://www.terabyteunlimited.com/index.htm](http://www.terabyteunlimited.com/index.htm)

---

### Post by fjkum on 2011-08-20
Excellent! It works!
Thanks.
Now I am a happy Ubuntuer...

---

### Post by walt.smith1960 on 2011-08-20
> **fjkum said:**
> Excellent! It works!
Thanks.
Now I am a happy Ubuntuer...

Now that you've created a backup, do you have space on your hard drive or do you have a spare hard drive to try a restore? If you REALLY needed to restore a partition and found out your backup was corrupt/wouldn't restore,  you would not be the first.  You may need to restore then reinstall GRUB or something like that.  It can be useful to find problems/tricks before you need to restore for real.

---

