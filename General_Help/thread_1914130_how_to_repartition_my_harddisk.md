---
title: "how to repartition my harddisk"
date: 2012-01-23
forum: General Help
---

### Post by roimekoi on 2012-01-23
[img]http://i57.photobucket.com/albums/g238/roimekoi/Screenshot.png[/img]
currently this is my partition snapshot,
/dev/sdb7/   is my root and /dev/sdb8/   is my home folder
Soon enough after downloading and installing some software(programming stuff and libraries)....  most of them ended in my root making it almost full therefore i wanted to free up some space in my home folder which is sdb8 and use it to merge with my root . but i found out that the unallocated space cannot be append to the root, after googling the problem, someone pointed out that this is because the unallocated space has a start and end sector that can only append to end of home folder. may i know if there is a way to solve my problem or else i can only backup my stuff and reformat and resetup most of my work.

---

### Post by varunendra on 2012-01-24
> **roimekoi said:**
> ..i wanted to free up some space in my home folder which is sdb8 and use it to merge with my root . but i found out that the unallocated space cannot be append to the root, after googling the problem, someone pointed out that this is because the unallocated space has a start and end sector that can only append to end of home folder.
As far as I know, it is not only possible, but also perfectly ok to resize your /home and merge the obtained space with root (/).

The problem you have described suggests that perhaps you are trying to 'shrink' the home partition from its 'right' end, while you need to have it on its left side to be able to merge it with root. While this can be easily done with gparted on a live cd, there is always a potential risk of loosing data or corrupting OS configuration or corrupting partitions that are being manipulated. Accordingly, here are two approaches I can suggest:

**1) _Try to create space without touching the partitions_:**
```
sudo apt-get clean
sudo apt-get autoremove
```
Additionally, you can remove any older kernels (after updating a fresh install, a newer kernel usually gets installed. If you are sure it works fine, the older one can be safely removed). This will give you another 100MB or so per kernel-image.

An easy way is to install synaptic (sudo apt-get install synaptic), open it (Alt+F2 > gksu synaptic), search for "linux-image" and "linux-headers". 'Completely remove' those which are older than the current one (for example, version 3.0.0.12 can be removed if 3.0.0.15 is installed and is working fine).

However, _be informed that it is always recommended to keep at least one previous kernel_ unless you are absolutely sure that everything works well with the latest one.

Also, consider creating a backup iso of the downloaded packages with aptoncd, in case you had to reinstall them.


**2) _If the above approach doesn't give you sufficient space, then_-**


[LIST=1]
[*]Download and burn clonezilla live cd
[*]Boot into clonezilla live and create a backup of your root partition (save it preferably on an external drive)
[*]Reboot into live mode using ubuntu live cd
[*]Move entire contents of the home partition onto an external drive (or the windows partition if no external drive is available)
[*]Run gparted and shrink the home partition from its left side so as to get empty space adjacent to the root partition. (since the partition is now empty, it should get shrinked immediately)
[*]Expand root partition to fill the just created empty space in its right side. ([COLOR=Red]!!Don't move the partition!! just resize it from its right end![/COLOR])
[*]Copy back the contents of the home partition from the backup.
[*]Reboot into installed Ubuntu and cross your fingers! ;)
[/LIST]
While the above operation 'should' finish smoothly without creating new problems, there is a possibility of a few minor issues that may arise. But since we have both the root and home partitions backed up, fixing it should be a piece of cake if a problem arises at all.


**_PS (Yet another approach)_:**

Apart from the above two approaches, a third one is to simply create a remastersys 'backup' dvd, remove and recreate partitions (I don't advise a separate home due to similar issues), and simply restore the backup from the live dvd onto the new partition. Fastest, and easiest! The only downside is - it will succeed in creating an iso only if the size of the stripped down (and maybe compressed) backup can fit on one DVD.

---

