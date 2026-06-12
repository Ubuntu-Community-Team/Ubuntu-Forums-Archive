---
title: "Mount Clonezilla Image for file retrieval"
date: 2012-06-21
forum: General Help
---

### Post by JediWebMaster on 2012-06-21
Hi All, I'm relatively new to Ubuntu and newer to Clonezilla but, been around computers a long time. Here is my sad story; appreciate any help:
 
I created an image of my Windows Home Server with Clonezilla and even a longer story but, I need to get some of the files off of the image. I've managed to setup an Ubuntu server and copy the image to a directory there. I found some help on mouting the image file to read at:
[http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/68_manually_partclone_restore.faq#68_manually_partclone_restore.faq](http://drbl.sourceforge.net/faq/fine-print.php?path=./2_System/68_manually_partclone_restore.faq#68_manually_partclone_restore.faq)
 
When I run the line:
sudo cat sbd1.ntfs-ptcl-img.gz.* |gzip -d -c | partclone.restore -C -s - -o sbd1.img
 
I get the error:
open logfile /var/logs/partclone.log error
 
and there is no file partclone.log. I'm stuck with my limited knowledge at this point. Has anyone run into this?
 
Thanks!

---

### Post by brianafischer on 2013-02-06
I just ran into this issue.  The solution is to run each piped command as sudo.  A non-root user cannot create files the /var/log/ directory.

```
sudo cat sbd1.ntfs-ptcl-img.gz.* | sudo gzip -d -c | sudo partclone.restore -C -s - -o sbd1.img
```

---

