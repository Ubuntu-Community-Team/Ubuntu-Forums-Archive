---
title: "File permissions error"
date: 2011-08-05
forum: General Help
---

### Post by dishvijay on 2011-08-05
Hello,

Very recently i installed Ubuntu 11.04 through WUBI on my laptop which already has a Windows 7 Enterprise. 

The only problem i am facing now is .. am unable to access - open/copy/anything - files that were under "My Documents" on Windows. When i logged back to Windows and checked, this folder appears to be in "green" color, from rest of folders. And any folders which were "green" under WINDOWS7 am not able to access them through Ubuntu.  

Am not sure if this is a "file permission" or "encryption" thing.

Is there any solution or workaround for this ? Have provided some screenshots. 

Please let me know if you need any other outputs.

---

### Post by gizmo720 on 2011-08-05
Try opening the terminal and cd-ing into the directory. Once there, try running ```
sudo cat list.txt
``` If that shows the text, than you have a permissions problem. If that is the case, try giving "Everyone" read/write access in windows, or chmod 777 it in linux. I'm not sure how well ntfs file permisions work under linux, as they have a fairly different security model. You may have better luck moving it to a FAT partition (although I am not sure how well that works either)

---

### Post by blind2314 on 2011-08-05
> **dishvijay said:**
> Hello,

Very recently i installed Ubuntu 11.04 through WUBI on my laptop which already has a Windows 7 Enterprise. 

The only problem i am facing now is .. am unable to access - open/copy/anything - files that were under "My Documents" on Windows. When i logged back to Windows and checked, this folder appears to be in "green" color, from rest of folders. And any folders which were "green" under WINDOWS7 am not able to access them through Ubuntu.  

Am not sure if this is a "file permission" or "encryption" thing.

Is there any solution or workaround for this ? Have provided some screenshots. 

Please let me know if you need any other outputs.

In Windows green usually means encryption. Do you have any encryption turned on? Also, if you right click and go to properties on the file, what do you see (in windows)?

---

### Post by dishvijay on 2011-08-07
> **gizmo720 said:**
> Try opening the terminal and cd-ing into the directory. Once there, try running ```
sudo cat list.txt
``` If that shows the text, than you have a permissions problem. If that is the case, try giving "Everyone" read/write access in windows, or chmod 777 it in linux. I'm not sure how well ntfs file permisions work under linux, as they have a fairly different security model. You may have better luck moving it to a FAT partition (although I am not sure how well that works either)
@gizmo720 - i tried to run your command and it displayed "NO such file or directory" so i tried to list another test file and got "Permission Denied". So i issued a "chmod 777 *" command inside "My Dcouments" folder and tried again still no good. So i checked on the permission thing just for that file every group has "rwx".

I could view all the files in other folders except for the "green" ones that would be "My Documents" and "Desktop".

Find the screenshot.

---

### Post by dishvijay on 2011-08-08
No I havent turned on any encryption, i checked too, also the file permissions have been set to "Everyone" in windows still no good. Not able to access any file under Ubuntu, the funny thing is only the two folders !! rest all fine.

Wondering if this has got to do something with the mount options ?

---

