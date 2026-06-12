---
title: "External Hard disk not readable on Windows"
date: 2011-09-15
forum: General Help
---

### Post by Friwise on 2011-09-15
Hi all!!
I have just bought an Apacer Ac203 500 GB. I formated it to NTFS and transfered all my important files from my laptop (it runs both ubuntu 11.04 and Windows 7 Ultimate 64 bit) and I am ready to format the laptop and turn it totally to linux ubuntu 11.04 and in November in 11.10.

I have a problem, though. Linux can read the Hard Disk but Windows (I tried windows on other laptops as well) say that I have to format the disj before using it.
Any idea what is going on?
Shall I save my files again somewhere else? Any idea how can I run the disk on Windows as well?

Thanks a lot

friwise

---

### Post by chromatica86 on 2011-09-15
Try formatting the drive to fat 32

---

### Post by alphacrucis2 on 2011-09-15
Or try formatting the drive as ntfs from Windows. Ubuntu will still be able to read/write it. It may be that Windows doesn't like the way parted or whatever linux tool you used to create/format the ntfs partition.

---

### Post by fdrake on 2011-09-15
in ubuntu ca you please post the results of
```
sudo fdisk -lu
```
so we can see exactly how your ntfs drive looks like.
try to change the ownership of the data. try to assign 777 (sudo chmod -R 777 /media/my_disk) . sometimes restrictions on permissions make windows fail to see/ edit the files.

---

### Post by Friwise on 2011-09-16
Thanks all!!!
I formated laptop in linux 11.04 and the hard disk works perfect. So now I have saved all data in laptop and I can format again the hard disk.
However fdrake's respond seems interesting. I did this sudo thing and I have the results but I have no idea how to post them. Can you guide me?
Thanks in advance

---

