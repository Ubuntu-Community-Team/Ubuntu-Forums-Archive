---
title: "Ubuntu 10.04 LTS NTFS file / directory corruption"
date: 2010-10-01
forum: General Help
---

### Post by errold32 on 2010-10-01
File corruption occurs when using ubuntu to write to a NTFS windows partition.

BUG or bad practice?

I am running ubuntu 2.6.32-25-generic on a partitioned HDD with windows 7. I made a directory in the windows partition with linux

Ex
6468af2f68AEFEC4 = windows partition

/media/6468af2f68AEFEC4/Users/OWNER/Desktop/stuff/new_folder

1 I put some files in new_dir with sftp

2 I then made a .odp presentation in stuff, and saved it. 

3 I then made a tar.gz in new_folder of the contents of new_folder.
tar -czvf test.tar.gz *

4 I then rebooted into windows, and both the directory (new_folder) and the presentation are corrupted. the directory was recognized at first, but had a permission problem. After I changed the windows permissions, the directory was not recognized as a directory any more, and the .odp presentation was opened as an ascii import file. 

The folder (new_folder) and the .odp are not deleteable, and (windows) chkdsk /f removes them.

is this behavior (corruption) a BUG or just bad practice?  

Thanks

---

### Post by dcstar on 2010-10-02
> **errold32 said:**
> File corruption occurs when using ubuntu to write to a NTFS windows partition.

BUG or bad practice?
........

Do a test by unmounting the drive before rebooting and see if things change.

---

### Post by errold32 on 2010-10-03
> **dcstar said:**
> Do a test by unmounting the drive before rebooting and see if things change.

Sorry, serious noob here, 

Do you mean do the above, and try writing to the ntfs partition again? Because chkdsk removed the corrupted directories. 

Before running chkdsk, i rebooted into both Linux and windows multiple times to try and gain access to my data. All attempts failed. 

Thanks

---

