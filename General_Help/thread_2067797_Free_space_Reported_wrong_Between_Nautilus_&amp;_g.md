---
title: "Free space Reported wrong Between Nautilus &amp; gparted"
date: 2012-10-07
forum: General Help
---

### Post by Redalien0304 on 2012-10-07
Nautilus  is Reporting 8.2GB on the File System in the screen shot Nautilus is  Reporting the wrong 
Free space compared Gparted or in the Cmd line. I am  using the Gnome Cinnamon Desktop I am Dual 
Booting Between Windows 7 &  Ubuntu 12.4
  Here is my free space on Nautilus
  [IMG]http://i.stack.imgur.com/8hEQq.png[/IMG][INDENT]   Here it is on Gparted would like to resize dev/sda7 (Ubuntu) which    is reporting 36.50 GiB free
 [/INDENT][IMG]http://i.stack.imgur.com/Oce3E.png[/IMG][INDENT]   Here it is on the CMD Line on /host Showing 37 G avail 8.2 used G
 [/INDENT][IMG]http://i.stack.imgur.com/WrFlo.png[/IMG]
                                                                                                                                                                                 any Solutions or ideas??

---

### Post by ajgreeny on 2012-10-07
Your screenshots do not make much sense to me.

Is this a virtual installation or a wubi install of Ubuntu (Ubuntu inside windows).  You have no ext# partitions showing anywhere in the shots you show here, so unless you have other disks with Ubuntu on which are not shown, I can't help any further.

---

### Post by mcduck on 2012-10-07
Just the normal difference between GB and GiB (and various programs using different units without using the new standard names for them).

Also keep in mind that available space on a partiton, and available space on a filesystem, are two different things, and also 5& of Ext filssystems are by default reserved to root use ronly and therefore doesn't count as available space if you check the availables space as normal user.

GParted screensot is irrelevant, and resizing the partiton wouldn't do much from Ubuntu's point-of-view, since that's a Wubi install and thus it's not using the partition directly.

---

### Post by coffeecat on 2012-10-07
@alien0304, you have a wubi installation which means that not all of your sda7 (44.65GiB) host partition is within your root fileystem. Wubi is installed to a virtual partition contained within a single file called root.disk in the NTFS filesystem. According to the output of df -h your root.disk is 14GiB (Gibibytes) in size with 7.7GiB free. 7.7GiB is equal to the 8.3GB (Gigabytes) showing in Nautilus. Nautilus is showing the free space in your root fileystem. Gparted is showing the free space in your host partition, sda7. These are not the same things and both Nautilus and Gparted are showing correct figures.

Part of the confusion is the varying reporting in GB (Gigabytes) and GiB (Gibibytes). 1 Gigabyte = 1,000,000,000 bytes. 1 Gibibyte = 1024 x 1024 x 1024 bytes = 1,073,741,824 bytes. Nautilus correctly shows GB for Gigabytes, Gparted GiB for Gibibytes and the terminal uses the shorthand "G" but is reporting in Gibibytes.

---

### Post by Redalien0304 on 2012-10-14
Ok Thanks everyone I reinstalled Ubuntu 12.04 on to a different partition no Wubi

---

