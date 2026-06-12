---
title: "External drive became marked as unallocated during conversion file system conversion"
date: 2009-09-08
forum: General Help
---

### Post by rubystallion on 2009-09-08
Hello,

I copy about 100 GB on my external hard drive to copy the files to a windows computer. As the disks were formatted as ext3, I couldn't open them in Windows, even Ext2IFS said the disk was completely unallocated. 
So I tried to convert the file system back to ext2, by running
```
tune2fs -O ^has_journal /dev/sdb
``` (according to [http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html"))
Still the file system was not recognized by Ext2IFS, so I tried to use gparted to convert the ext2 file system to ntfs. 
After a few seconds, gparted cancelled the operation, stating an error about the disk label (I'm not sure I remember the error correctly). 
Now the disk is shown as unallocated. 
As gparted only ran a few seconds, I'm quite sure no data was deleted. Is there a fast and reliable way to recover the file system or would it be less hassle to just format the drive as ntfs and copy all the files again? If not, why is it not possible?

Thanks in advance!

---

