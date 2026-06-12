---
title: "Removing the Ubuntu Partition"
date: 2012-09-16
forum: General Help
---

### Post by Seth.Meyers on 2012-09-16
Hi.
I'm using a self-built computer running Windows 7 on a 128GB SSD, and I also have a 1TB HDD for storage. Recently, I installed Ubuntu on a 24 GB partition on the storage drive using Wubi. I then made the mistake of deleting the Ubuntu and Wubi folders off of the Windows partition. This made it so I couldn't boot into Ubuntu at all, but the partition is still there and it still asks me which OS I want to boot into on startup. I've tried Windows Disk manager (doesn't see the partition), Gparted (also doesn't recognize the partition), and booting into Ubuntu to solve the problem (I can't boot into Ubuntu.)

Please help me get rid of this partition and reclaim my hard drive as sovereign territory!

---

### Post by jerrrys on 2012-09-16
Its not a partition.

[https://help.ubuntu.com/community/Wubi#Un-install_from_Vista_or_Win7](https://help.ubuntu.com/community/Wubi#Un-install_from_Vista_or_Win7)

More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+uninstall+wubi&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+uninstall+wubi&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

And welcome to the forums :)

---

### Post by oldfred on 2012-09-16
If you manually deleted the wubi files, you may just have to manually delete the Windows boot entry. Use bcdEdit in Windows to edit the BCD to remove the wubi entry.

With a large data partition, you might want to read this, I follow his logic but allocate a bit more and do a full install of Ubuntu.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by Seth.Meyers on 2012-09-16
Thanks for the helpful replies. I used BCD to remove the Ubuntu install from the boot menu, and automatically boot Windows. But the 24 GB is still missing from my storage drive, and Disk Manager does not see the full capacity of the drive. It would be ideal if I could get full capacity of my drive back.
If there's a solution, I'd be happy to hear it.

Thanks again!

---

### Post by oldfred on 2012-09-16
Did you create a separate NTFS partition for the wubi install? Or if just deleted how did you delete it? In Ubuntu you have to empty the trash before space is available again. In Windows you may need to houseclean partition?

---

### Post by Seth.Meyers on 2012-09-16
> **oldfred said:**
> Did you create a separate NTFS partition for the wubi install? Or if just deleted how did you delete it? In Ubuntu you have to empty the trash before space is available again. In Windows you may need to houseclean partition?

I made the mistake of deleting the folders marked Ubuntu and Wubi on the D (storage) drive. I then emptied the recycle bin.

What do you mean by "houseclean"? Please explain further, I'd love to be able to solve this problem.

---

### Post by oldfred on 2012-09-16
If you deleted root.disk and emptied recyle bin, d: should be fully available again. I do not understand why there is an issue? The root.disk is just a file like any other file in Windows.

---

### Post by Seth.Meyers on 2012-09-16
> **oldfred said:**
> If you deleted root.disk and emptied recyle bin, d: should be fully available again. I do not understand why there is an issue? The root.disk is just a file like any other file in Windows.

There's no root.disk file anywhere in the D drive. It's weird, I know.

---

### Post by oldfred on 2012-09-16
Do you have Ubuntu liveCD or gparted LiveCD?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)


And then what does gparted show?

---

### Post by Seth.Meyers on 2012-09-16
> **oldfred said:**
> Do you have Ubuntu liveCD or gparted LiveCD?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)


And then what does gparted show?

gparted shows all my disks and partitions, except that my D drive is still 24 GB short, leading me to believe that there's a hidden partition.

---

### Post by oldfred on 2012-09-16
From liveCD click on all your c: & d: partitions to mount them.

Then from terminal run these:

df -Th

sudo fdisk -lu

---

