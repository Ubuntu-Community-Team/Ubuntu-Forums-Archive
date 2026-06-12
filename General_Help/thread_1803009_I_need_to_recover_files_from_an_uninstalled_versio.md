---
title: "I need to recover files from an uninstalled version of ubuntu"
date: 2011-07-12
forum: General Help
---

### Post by tostrye on 2011-07-12
I had 10.04 installed using wubi. I used it only for pictures. I uninstalled that version and installed 11.04 as a true dual-boot. I  forgot to back up some pictures on the 10.04. Is there a way to recover them?

---

### Post by wildmanne39 on 2011-07-12
Hi, not that I am aware of since it was installed in wubi.

---

### Post by seawolf167 on 2011-07-12
Since it was a Wubi installation, when you uninstalled it the virtual partition containing Ubuntu would have been deleted with all contained data

---

### Post by doas777 on 2011-07-12
since the file was deleted inside of windows and formerly existed on the windows disk, then you want a windows undelete utility. you could try [recova]("http://www.piriform.com/recuva"), as it is free.

Here is the community documentation on Data Recovery:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

the formal way to recover data, is to:
1) immediately shut down the machine.
2) boot off a live CD, and make an image of the drive that is missing the file. write this image off to another drive of greater or equal size.
3) reboot into windows, and attempt to recover the file off of the second drive.

you can just skip to #3, but if you do, you run a greater risk of losing the data you want to save. you are at a particular disadvantage because the file you wish to undelete is very large and is likely to have been at least a little overwritten since the deletion. 
If you do choose to recover off a running install, be sure you do not recover the file to the same partition it was deleted off of. you will likely overwrite parts of the file with the parts you are recovering, and in the process doom the operation to permanent failure.
It is unfourtunate that the problem involves a wubi install, or I'd just suggest photorec.

Once you have recovered the ubuntu virtual hard disks (c:\ubuntu\*.disk) you need to open the virtual filesystem and extract the files you wish to save. this should help:
[http://suhothayan.blogspot.com/2010/03/mounting-disk-files-on-ubuntu.html](http://suhothayan.blogspot.com/2010/03/mounting-disk-files-on-ubuntu.html)

---

