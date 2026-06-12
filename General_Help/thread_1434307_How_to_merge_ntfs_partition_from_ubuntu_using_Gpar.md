---
title: "How to merge ntfs partition from ubuntu using Gparted?"
date: 2010-03-20
forum: General Help
---

### Post by karthick87 on 2010-03-20
I have a free space of nearly 20GB,i want to merge these free space to another partition(/dev/sda1)..I have attached a snapshot here..Some one help me..!

---

### Post by johngreth on 2010-03-20
First, back up everything important on sda1 because resizing partitions, especially ntfs partitions, can corrupt them and you would loose all your data. Second, right click the drive and click Resize/Move. Then set the free space following to 0, click Resize/Move, and apply all operations. Don't stop this process no matter what or it will ruin the data.

This is very risky and I don't suggest it unless you really need the space, have a backup, and are prepared to reinstall windows and all your applications.

---

### Post by roccivic on 2010-03-20
If Vista is installed on /dev/sda1, you are guaranteed not to be able to boot it again after resizing.

Best thing to do is to back everything up. Delete that partition and make a clean new one.

---

### Post by cd-r80 on 2010-03-20
From Windows if your partition is not seen after Gparted.

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by oldfred on 2010-03-20
You can use the latest gparted but have to make sure you do not move the start of the partition if it is Vista or 7. 

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the [COLOR=Red]round to cylinder unchecked.[/COLOR]
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)
Vista and Partitioning - details
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

---

