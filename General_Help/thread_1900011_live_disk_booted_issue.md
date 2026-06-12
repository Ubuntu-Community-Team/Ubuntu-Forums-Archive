---
title: "live disk booted issue"
date: 2011-12-25
forum: General Help
---

### Post by abhisek7 on 2011-12-25
Hi,

Please help any one urgently. Last few days I am heading to a issue with Live Disk.
I mean I follow the steps  ( Link - [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch) ) to create a .iso image of ubuntu karmic distro. Then I installed it into hardisk into /dev/sda1 partition using usb-creator-gtk. The partion of /dev/sda like:

1) /dev/sda1 -- 169 GB -- I
2) /dev/sda2 -- 75 GB 

When I booted from the hard disk , I found the following with (df -h)

aufs              /
udev             /dev
/dev/sda1     /cdrom  --> 169GB of which 1% used
/dev/loop0    /rofs      --> It shows the size 289MB which is full

The problem  start when I found the error "/var/lib/mysql"  during mysql server starting. Also I found that there is no space even to create a file, though I have used only 1% of the partition. Can you please know me how I can use the total space of /dev/sda1 where I actually install my image.

Thanks

---

### Post by dino99 on 2011-12-25
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

note: you might choose a recent release like Oneiric, yours is outdated & no more alive.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by West201 on 2011-12-25
Can you please tells more info about your hardware ? Follow dino99's advice and go with a recent release. Try 10.04 LTS

---

