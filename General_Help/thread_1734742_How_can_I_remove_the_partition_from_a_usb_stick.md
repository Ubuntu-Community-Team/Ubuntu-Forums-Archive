---
title: "How can I remove the partition from a usb stick"
date: 2011-04-20
forum: General Help
---

### Post by Alan5 on 2011-04-20
I have booted from live ubuntu usb sticks, 8GB size. There were problems which is why there are two. I wish to reclaim one of these for genereal use.

Please, how do I remove the partition ?

Before coming here I searched by google, The advice is format the stick under Windows. This does not work.

My thanks.

---

### Post by ttshivers on 2011-04-20
You can delete a partition on a flash drive just like deleting a partition on any other storage device.  Here is an article explaining how: [http://www.ehow.com/how_7331108_delete-ubuntu-installed-external-hdd.html]("http://www.ehow.com/how_7331108_delete-ubuntu-installed-external-hdd.html")

---

### Post by Ad@m on 2011-04-20
You should be able to delete and format the partitions in Windows by using 'Disk Management'

Right click on My Computer > Manage > Disk Management

---

### Post by C.S.Cameron on 2011-04-20
I blame two bricked flash drives on trying to format in Windows.
Windows does not like multi partition flash drives.

Use gparted if you have more than one partition.

---

### Post by Alan5 on 2011-04-21
My thanks to all contributors. I will report how they work.

---

### Post by Alan5 on 2011-04-21
I tried the suggestion of ttshivers described at the eHow site. I was running ubuntu off another memory stick. The process didn't work.

The partitiioned drive showed a usable memory of 7.4 GB . Empty and unpartitioned it would show 8.0 .

The method is : plug in the device then : System > Administration > Disk Utility > Peripheral Devices . Select the drive.

This utility appears excellent. In the lower part of the pane Delete Partition produces "The device is busy," so Unmount the partition then Delete it. The lower part of the pane showed that there is no partition. The drive was present, showing the 7.4 GB . To reclaim the full memory I clicked on Format , which produced the 8.0 .

The snag is that the stick is now invisible under ubuntu and fedora. Windows can see drive F: , but tells me to insert a disk. Even the Disk Utility cannot find it.

I suspect the Format command, because this should take what it finds and deliver a useful drive..

I am losing appetite for this.

---

### Post by gamebusterzade on 2011-04-21
use gparted

u may need to create a new partition table (will wipe the entire USB)
edit:its under device

then partition away

---

### Post by samacaster on 2011-04-21
Windows will only recognise the 1st partition of removable media. Ubuntu should "see" both, as to why its not, who knows.

Download and use a dedicated partition manager such as Gparted. Use this to delete partitions from the USB stick. Then you can add all the partitions you want.

---

### Post by C.S.Cameron on 2011-04-21
You are lucky the drive still works after using Windows to format.
Use gparted for multi-partition flash drives in the future.

---

