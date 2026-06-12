---
title: "Can't write to external hard drive? please help"
date: 2009-11-24
forum: General Help
---

### Post by jonnytb on 2009-11-24
So I have an external hard drive (500gb WD passport) I use to move stuff between my computers (2 running windows, 1 ubuntu laptop) and since I hooked it up to ubuntu to listen to music I can't write anything to it, on neither ubuntu or windows. I believe it has something to do with ubuntu's security permissions. I need it to be able to read and write under both ubuntu and windows and go back and forth. 
any help is appreciated
thanks in advance
jonny

---

### Post by voteforcondit on 2010-01-02
i need help with this also 
i have a my passport 320gb

---

### Post by jonest1 on 2010-01-02
By default, an external usb disk is going to be available in /media and will only allow root to write to it.  The quick way to allow access is to create a subdirectory and then give yourself ownership of the directory and you should be good to go.

So, I have an external drive I use for backups at /media/ext1tb.  The ownership is root:root and permissions are rwxr-xr-x or 755.  So, as my normal user, I can read, but not write.  I then created a subdirectory called backup and gave myself ownership.
```
sudo mkdir /media/ext1tb/backup
sudo chown username:groupname /media/ext1tb/backup
```
At this time, I'm not aware of how to change the ownership rules to allow me to own the actual device, but this should get you going.

---

### Post by scouser73 on 2010-01-02
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by Cheesemill on 2010-01-02
> **scouser73 said:**
> **1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

This wont work. NTFS drives don't understand Linux permissions, the entire drive is granted the permissions you specifiy either in fstab or with the mount command.

---

