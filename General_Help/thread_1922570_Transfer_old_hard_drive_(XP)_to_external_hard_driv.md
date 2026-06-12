---
title: "Transfer old hard drive (XP) to external hard drive"
date: 2012-02-09
forum: General Help
---

### Post by madeoforanges on 2012-02-09
Hi there,

I've been searching google and this forum and it's getting me overwhelmed with information.

I would like a straight forward procedure to transfer files from my old hard drive, which is running windows XP to my external hard drive. Ubuntu is the middle man. I heard about VirtualBox, but I don't want to do anything without some advice from Ubuntu guru's here.

Advise.

-orange :)

---

### Post by sikander3786 on 2012-02-09
Hi. :)

You simply want to copy over the data from your old HDD or also want to copy the Windows XP install?

If you just want to copy the data, you can simply download Ubuntu and create a Live USB. Boot it and copy your files just like you would do in Windows.

If you want to copy the XP install too, you can use Clonezilla to clone the whole HDD or its partitions.

[http://www.clonezilla.org](http://www.clonezilla.org)

We can give you precise instructions on how to go about any of those methods once you tell us what you want to achieve exactly.

---

### Post by madeoforanges on 2012-02-09
Hi,

I don't need Windows XP, I just want to files aka photos, movies, and etc.

-oranges

---

### Post by forrestcupp on 2012-02-09
If you can boot to XP, just plug in your external drive and open up Windows Explorer and copy the files over.

But since you're asking about using Ubuntu, I assume that you can't boot to XP on that computer. So you need to do what sikander3786 said either create a LiveCD or bootable USB drive of Ubuntu to boot to on that computer. If you go to [http://www.ubuntu.com](http://www.ubuntu.com) it tells you how to download the ISO file and get it on a CD or create a bootable USB drive.

When you get that done and boot to Ubuntu on that computer, you will see a panel of icons on the left side of the screen. One of the top ones should be a Home folder icon; click that one. This is called Nautilus and it is similar to Windows Explorer or My Computer in Windows. On the left side of that screen, you should see a section called Devices that should show your XP drive, and your external drive if it is plugged in. 

In Linux, these drives have to be mounted before they can be used. Just clicking on one should automatically mount it and bring up the filesystem. Then you can just copy your files from your XP drive to the external, just like you would with Windows Explorer or My Computer.

---

### Post by winh8r on 2012-02-09
> **madeoforanges said:**
> Hi,

I don't need Windows XP, I just want to files aka photos, movies, and etc.

-oranges

Obtain a Ubuntu Live cd by downloading an.iso file and burn it to a cd-rom.

plug external drive into computer.

place Live cd in cd drive and reboot computer.

Ubuntu will run from cd drive and allow you to move whatever you want from the drive containing XP files over to external drive.

It is assumed that you cannot boot the drive with XP on it and simply copy them across that way, is this correct?

If you have Ubuntu installed on your computer already then you can set the XP drive as a slave and copy files from it that way.
eg Ubuntu is the primary master drive which is used to boot and the XP drive is the primary slave allowing you control over the XP drive to transfer files to your external drive.


If none of this is useful, please give a detailed explanation of what you have installed at the moment and exactly what you are trying to achieve.

Hope this helps you.

---

