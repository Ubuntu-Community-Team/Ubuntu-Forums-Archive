---
title: "reallocate space on a ubuntu win7 dual boot"
date: 2011-02-26
forum: General Help
---

### Post by samir.raj on 2011-02-26
I installed ubuntu on my computer which had windows 7 pre installed.I mistakenly alloted very less space to ubuntu.And now the space is full. Is there a way to reallocate disk space??

---

### Post by sviola on 2011-02-26
You will need to boot from your Ubuntu Live CD, which you used to install Ubuntu. Once you have booted from it, here are the steps to resize your partitions:

[LIST=1]
[*]Instead of installing, click "Try Ubuntu" (assuming you are using a 10.10 Live CD). This should take you to the desktop.
[*]Open GParted Partition Editor by going to System > Administration > GParted Partition Editor
[*]From there you will be able to resize any of your partitions.
[/LIST]
I hope that helps!:)

Edit:
Just in case you don't know how to resize your partitions once your in GParted Partition Editor, take a look at the page on the Ubuntu wiki on [how to resize a partition]("https://help.ubuntu.com/community/HowtoPartition/ResizingPartition").

---

### Post by seawolf167 on 2011-02-26
Windows 7 comes with its own [partition editor]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/"), I highly suggest using that to resize its own NTFS partition to ensure that everything goes smoothly. You can definitely use a program like GParted, but I've had better luck when using Windows tools to do that particular resize.

---

### Post by Paradoxfox93 on 2011-07-06
11.04/win7 brand new laptop, same issue.  No disks or anything for win7 but gparted resized for the install well enough so i'm going to give it a go again only required a chkdsk by win7.  Will report back later today.

---

