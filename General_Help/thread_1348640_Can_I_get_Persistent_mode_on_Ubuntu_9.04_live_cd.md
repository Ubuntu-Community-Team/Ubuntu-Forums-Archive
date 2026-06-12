---
title: "Can I get Persistent mode on Ubuntu 9.04 live cd"
date: 2009-12-07
forum: General Help
---

### Post by checoimg on 2009-12-07
Hi and thanks for your time! :)

I already formatted a USB memory as Casper-cow so I could use it with persistent mode like I read about Dapper Drake but downloading the Dapper Drake will add more downloading time so my objective is to get this with the Ubuntu 9.04 Live CD.

---

### Post by checoimg on 2010-12-25
If you want to get persistent mode you can get it on a USB with this app

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

you will need the ISO image

---

### Post by C.S.Cameron on 2010-12-25
Casper-cow partitions worked with early versions of Ubuntu.
Now days you need to name the partition casper-rw.
home-rw will give a persistent home partition.
With the 10.10 CD you need to hit something like Shift or Tab or Esc or something to get to the screen where you can press F6 and add <space>persistent.

---

### Post by C.S.Cameron on 2010-12-25
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

