---
title: "How can I put documents to other partition ?"
date: 2012-04-14
forum: General Help
---

### Post by DaviesX on 2012-04-14
A fresh installed Ubuntu would put Documents, Public, Downloads in the partition where the system located in. But I want to separate the documents from operating system. How can I do that ?

Thank you.

---

### Post by Jacobonbuntu on 2012-04-14
Hi DaviesX, on installation, create a separata partition with mount point /home. all files will be put there.

edit: choose "something different" (free translation from Dutch :)), then create a root partition for your system (mount point "/"), a swap partition (let's say 4gb) and a /home partition. be sure to leave the /home partition untouched on the next installation if you want to keep your documents. The down side is that it is usually not a good idea to keep all setting files on the next install (also located in your home folder)

---

### Post by oldfred on 2012-04-14
There are several ways, I use links. You do have to create a mount for the data partition that has your documents (I now have 13 or 14 folders in my data partition). Then you can link a folder to your /home. I use this primarily as I am multi-booting and want the same data available from all systems.

Splitting home directory discussion:
Detailed example in post #4, but see others comments.
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by DaviesX on 2012-04-14
Can you please provide more detail ? I am not clear yet. Thank you

---

### Post by Jacobonbuntu on 2012-04-14
sorry, I edited my first reply for more info :)

---

### Post by DaviesX on 2012-04-14
Thank you ^_^

---

### Post by haqking on 2012-04-14
you can just edit the user-dir.dirs file to point the documents or pictures or whatever to wherever you like

saves relocating home etc

peace

---

### Post by callmemahavir on 2012-04-15
METHOD 1 : Check it is possible to mount the partition in Linux.

METHOD 2 : Download Virtualization tools and run other partition OS.

METHOD 3 : Copy the data to CD-ROM or Pen drive and access it in other OS.

---

