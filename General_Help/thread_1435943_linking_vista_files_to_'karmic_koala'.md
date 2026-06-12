---
title: "linking vista files to 'karmic koala'"
date: 2010-03-22
forum: General Help
---

### Post by poopookakada on 2010-03-22
sorry if this has been posted before, i've looked around and not found it. also sorry if it's in the wrong place, but i couldn't decide where to post it :)

basically i was wondering if it's possible to link the documents, music, etc from vista with karmic koala. i have both operating systems on my laptop and need to access the files on vista through my ubuntu.

if anyone can help me out it'd be greatly appreciated

---

### Post by byStanderone on 2010-03-22
...not sure what you meant by linking files between the two 'os', but you can mount your vista in ubuntu...and access it. under places, clik on your vista filesystem.

---

### Post by prodigy_ on 2010-03-22
Can you access your NTFS (Vista) partition from Ubuntu at all? Does it appear on your desktop automatically when you login? If yes, you'll only need to edit bookmarks in File Browser (Nautilus). There's "Bookmarks" menu for that.

Otherwise open Terminal and type: ```
cat /etc/fstab
``` Post the output here. Then type: ```
sudo fdisk -l
``` Again, post the output here.

---

### Post by wqawasmi on 2010-03-22
One thing you can do is actually link the files you wan't into convienient icons onto your desktop.

Open up a terminal and type the following:

```
 ln -s /directory/of/file nameOfNewFile 
```

Think of Symbolic Links as Icons in windows.

---

### Post by poopookakada on 2010-03-22
> **prodigy_ said:**
> Can you access your NTFS (Vista) partition from Ubuntu at all? Does it appear on your desktop automatically when you login? If yes, you'll only need to edit bookmarks in File Browser (Nautilus). There's "Bookmarks" menu for that.

Otherwise open Terminal and type: ```
cat /etc/fstab
``` Post the output here. Then type: ```
sudo fdisk -l
``` Again, post the output here.

no i can't access the vista partition at all

result for ```
cat /etc/fstab
``````
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
```result for ```
sudo fdisk -l
``````
[sudo] password for tim: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19255b7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18329   147223520+   7  HPFS/NTFS
/dev/sda2           18329       19255     7435264    7  HPFS/NTFS
/dev/sda3           19255       19458     1626112    7  HPFS/NTF
```

---

### Post by prodigy_ on 2010-03-22
Ahh, you installed Ubuntu with Wubi. :-) Read [this HOWTO](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?) then.

---

### Post by gadolinio on 2010-03-22
If you installed ubuntu with wubi, your " C : \ "  drive is mounted (when in ubuntu) in /host.
So if you want to access your files inside, let's say, C : \ Documents and settings \user\documents,
you have to go to /host/documents and settings/user/documents.
That's the same folder you see in windows. 
To create a bookmark (which will appear on the left, with your Places in nautilus):
once in that folder, go to Bookmarks menu, and click "add bookmark".
You'll see it appear under places.

To create a link:
once in the folder of your interest, go one level up to its parent directory (eg /host/documents and settings/user ), right click the folder you want to access, and choose "create link".
The link will appear; cut and paste it to wherever you want.

---

### Post by poopookakada on 2010-03-22
> **gadolinio said:**
> If you installed ubuntu with wubi, your " C : \ "  drive is mounted (when in ubuntu) in /host.
So if you want to access your files inside, let's say, C : \ Documents and settings \user\documents,
you have to go to /host/documents and settings/user/documents.
That's the same folder you see in windows. 
To create a bookmark (which will appear on the left, with your Places in nautilus):
once in that folder, go to Bookmarks menu, and click "add bookmark".
You'll see it appear under places.

To create a link:
once in the folder of your interest, go one level up to its parent directory (eg /host/documents and settings/user ), right click the folder you want to access, and choose "create link".
The link will appear; cut and paste it to wherever you want.


cheers for that!! exactly what i was after... i KNEW there'd be a way to do it, but couldn't quite work out what folder it would be in ;)

will mark as solved now :D

---

