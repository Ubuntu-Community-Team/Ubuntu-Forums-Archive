---
title: "Resizing external drive without lost data"
date: 2006-04-24
forum: General Help
---

### Post by peyu on 2006-04-24
Hi everybody,

I just buy an external drive with one ntfs partition and because of time, I didn't clear the partition to create a new fat32 one.

Now, I've got about 30Go of data on the ntfs part (and 130Go free, so 160 Go in total), and I want to switch the entire disk to fat32 to have the possibility to read/write with ubuntu. So my idea was to resize the ntfs part to something like 100Go, create a fat32 part with the 60Go free, copy all the data from the ntfs to the fat, and then delete the ntfs and resize the fat32 to take the entire size.
Ok, this is the theory part...

But in the real life, I plug the usb drive, ubuntu automount the ntfs partition, so I unmount it. With GParted, It cannot resize the ntfs partition, and with Qparted, when it analyses /dev/sda1 , and Qtparted told me that the ntfs support is not implemented yet..

Any ideas ? I will be pleased to hear it...
Thanks

---

### Post by sinkxdie on 2006-04-24
Ouch, try using NTFS Tools or something like it to transfer all the data to a partition of your HD in and then transfering that data back to the formatted Fat32 on the external drive if possible. Just a suggestion. :D

---

### Post by peyu on 2006-04-24
Thanks for your suggestion, but I haven't any other hard drive with 30Go free...
After looking some webs, I discover that I installed with synaptic Qtparted 0.4.4, but Qtparted 0.4.5 exists ! I see it on the official website..

So i tried to download the tar.gz, but I cannot "configure" it because it tolds me that libuuid is not installed, but in synaptic it's installed... I don't understand, but I'm a newbie...

Well, maybe I will download Partition Magic and try to use it, or find a disk with 30Go free... But if anybody have a new idea...

---

### Post by sinkxdie on 2006-04-24
Did you try the Ubuntu LiveCD GParted?

---

### Post by peyu on 2006-04-24
No, but I try it in Ubuntu Breezy installed on my laptop.. Is there a difference ?

---

### Post by sinkxdie on 2006-04-24
Yes, when you do it from the LiveCD it has full access and control. You can't make changes to a disk when it is in use. :D

---

### Post by peyu on 2006-04-24
Yes, I know that, that's why when I plug the usb drive, Ubuntu automount it and I unmount it. And Then I start Qtparted to make the changes...
But there is something strange :

I start Qtparted in a console using
```
sudo qtparted
```
In the Qtparted window, I see 2 drives : /dev/hda and /dev/sda
When I click on /dev/sda1, I've got a new nautilus window (the same way when you plug an external drive and Ubuntu automount it) BUT it tolds me that it can't show the content of "mntqp", and then qtparted crashs, with a message in the terminal : ```

No implementation : the support for the opening of ntfs file system is not yet implemented
Segmentation error
```

---

### Post by sinkxdie on 2006-04-24
Oh, I forgot to tell you that NTFS is not so well with Linux. Your going to have to install NTFS tools or whatever it's called.

---

