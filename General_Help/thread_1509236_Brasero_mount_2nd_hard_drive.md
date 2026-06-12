---
title: "Brasero mount 2nd hard drive"
date: 2010-06-14
forum: General Help
---

### Post by wbs95662 on 2010-06-14
I would like to know how to get brassero to look at my 2nd hard drive I can only see my main HD. I have music files on my other drive.

---

### Post by garvinrick4 on 2010-06-14
To get anything to see a drive it must be mounted first. Look under Places drop down menu and see if it is there then click on it. If not run this code and see if it is there under sdb.

```
sudo fdisk -l
```  (that is a small L)

If it is not there run this.

```
sudo apt-get install gconf-editor
```Go to Applications to System Tools to Configuration Editor. Open it. go to Apps to nautilus to preferences and see if the auto_mount is checked and auto-open if you also want.

Should be somewhere in one of these fix's. But anyway around it a drive must be mounted to be seen or used. If a drive has a Operating System on it unmount it before shutting computer down.

---

