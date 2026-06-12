---
title: "Yet another resizing partition problem"
date: 2009-07-06
forum: General Help
---

### Post by desperateone on 2009-07-06
I'd like to take 15GB from my 60GB Windows XP ntfs boot partition, but Gparted refuses to resize. I'm doing it from under Ubuntu, unmount the XP partition, but the move/resize option is faded. I shouldn't need a Gparted Live CD, should I? Or maybe there is a tool to do this from under Windows somehow?

---

### Post by Augsburg on 2009-07-06
Have you tried defragmenting the hard disk? I'm not certain this will do the trick, but I know one method for making it easier and faster to create a separate partition is to have more consecutive free space on the disk.

You can defrag the disk by selecting start > and right click on "My Computer". Select "Manage".  Choose Disk Utilities and select Defrag.

---

### Post by blues2use on 2009-07-06
I used Easeus Partition Manager under XP to resize my partition. It's free and it works. I've also used Gparted and it worked as well. Easeus may be a better option for you at the moment...

[http://www.partition-tool.com/](http://www.partition-tool.com/)

Hope this helps...

---

### Post by desperateone on 2009-07-06
> **blues2use said:**
> I used Easeus Partition Manager under XP to resize my partition. It's free and it works. I've also used Gparted and it worked as well. Easeus may be a better option for you at the moment...

[http://www.partition-tool.com/](http://www.partition-tool.com/)

Hope this helps...

Defragging did nothing, but this program did the trick, thanks.

---

### Post by synapsys on 2009-07-06
You can do it from ubuntu. Gparted needs the package ntfsprogs to be able to resize ntfs partitions.

```
sudo apt-get install ntfsprogs
```

---

