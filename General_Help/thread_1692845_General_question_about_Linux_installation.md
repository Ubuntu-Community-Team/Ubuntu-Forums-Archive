---
title: "General question about Linux installation"
date: 2011-02-22
forum: General Help
---

### Post by JohnElway on 2011-02-22
I've already installed Ubuntu multiple times, but I have a question about why a certain procedure is recommended. In all the installation guides I always see people installing to multiple partitions, i.e. creating separate partitions for "/", "/home" and swap, but what is the purpose of this? My only guess is that it makes it easier to do reinstalls because people can leave their home partitions as is and install over the root and swap partitions (but then what's the purpose of keeping the swap and root partitions separate?). 

Also, I keep all my personal data on an external hard drive, so my home partition never has much on it anyways. With this in mind, would there be any reason not to install Ubuntu on a single partition when I do future installations?

---

### Post by tea for one on 2011-02-22
In order to help you decide, have a quick look at the contents of the hidden folders in your /Home directory.

Places > Home Folder > View > Show Hidden Files.

There are many personal application settings here over and above your personal data (Music & Documents etc) on your external drive.

Of course, you can nominate your external drive to contain your complete /Home Folder.

---

### Post by sikander3786 on 2011-02-22
There is no reason not to install Ubuntu or any Linux to a single partition except for own convenience. In fact, default install of Ubuntu by choosing "Use entire partition" ends up in '/' and a swap partition only. There is no separate /home partition.

But as you mentioned, /home saves you some troubles while re-installing. If you don't want to preserve your settings and there is no personal data in /home, you can just re-install to the '/' partition.

If you don't want to hibernate/suspend and have large amounts of RAM, a swap partition is also not absoulutely necessary. Mean you can just install Linux to a single '/' partition as you install Windows to a C: drive or so.

This might help.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

---

### Post by dcstar on 2011-02-22
> **JohnElway said:**
> I've already installed Ubuntu multiple times, but I have a question about why a certain procedure is recommended. In all the installation guides I always see people installing to multiple partitions, i.e. creating separate partitions for "/", "/home" and swap, but what is the purpose of this? My only guess is that it makes it easier to do reinstalls because people can leave their home partitions as is and install over the root and swap partitions (but then what's the purpose of keeping the swap and root partitions separate?). 


Separate partitions mean that the respective filesystems are isolated.

The major benefit of this is when a disaster situation occurs - like a power failure during a disk write - then any potential damage is limited to the particular filesystem being written to at that moment.

If you have only one big filesystem then you are virtually guaranteed to damage your whole system when the disaster occurs, if you have more than one filesystem then the damage will be limited to only one of them - the chances of losing data is reduced. There are also performance benefits from having separate filesystems.

Swap can be constantly written to in a lot of systems, having it in the root filesystem just multiplies the chances of damage to that vital filesystem in the event of problems. Swap can also be shared by booting multiple Linux distros, so instead of wasting space in each root filesystem is make much more sense to have one common location (just** don't** hibernate one system and boot another that will overwrite the same Swap filesystem).

---

