---
title: "External Drive problems"
date: 2010-02-28
forum: General Help
---

### Post by charlton2142 on 2010-02-28
Hey Im trying to transfer some of my files on my external hard drive but I am not able to access some seemingly random folders because I don't have permission. I think that my file system is fat32 if that helps at all. I have tried chown and chmod but to zero avail. please help me with this problem thanks

---

### Post by karatedog on 2010-02-28
FAT32 shouldn't store user or group privileges.

Unmount the drive, and run: 
fdisk -l 
and paste the results here (or just figure out if it is really a FAT32 drive)

---

### Post by scouser73 on 2010-02-28
> **charlton2142 said:**
> Hey Im trying to transfer some of my files on my external hard drive but I am not able to access some seemingly random folders because I don't have permission. I think that my file system is fat32 if that helps at all. I have tried chown and chmod but to zero avail. please help me with this problem thanks

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

