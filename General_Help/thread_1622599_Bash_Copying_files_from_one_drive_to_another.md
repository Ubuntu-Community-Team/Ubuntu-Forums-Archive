---
title: "Bash Copying files from one drive to another"
date: 2010-11-15
forum: General Help
---

### Post by thehomicidal on 2010-11-15
Howdy,

I've got two external hard drives, a 2TB and a 320GB. I've recently come from Windows 7. On Windows 7 I wrote a batch file which checked whether both hard drives existed and then copied a couple of folders from the 2TB to the 320GB without overwriting. I've been trying to work out how to do the same under Linux without much luck. Could someone point me in the right direction? I've tried rsync but it looks like it overwrites. Does rsync overwrite? Can someone suggest another way of doing it?

If it helps, the batch file I wrote in Windows 

if exist D:\320GBDrive (if exist H:\2TBDrive (xcopy H:\2TBDrive\* D:\320GBDrive /I/E /-Y < C:\decline_copy.txt)) 

Which basically checks for drive D:, checks for drive H: and then copies the contents of the folder on drive H to drive D and says no every time it asks to overwrite.

---

### Post by galvatron408 on 2010-11-15
rsync is the tool for you. Just use the update argument with rsync so that it doesn't overwrite.

---

### Post by thehomicidal on 2010-11-15
Thanks for the quick reply! :)

I've just put the update command in and now it doesn't copy anything. I've removed a file from the 320GB hard drive and it still doesn't work. Would the fact that there are subfolders be something to do with it?

---

