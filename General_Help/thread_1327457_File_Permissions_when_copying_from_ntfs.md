---
title: "File Permissions when copying from ntfs"
date: 2009-11-15
forum: General Help
---

### Post by fr34k on 2009-11-15
i have set a custom umask in .bashrc and .gnomerc

but this are not applied when i copy files from an NTFS pendrive to my Ext4 harddisk . files are copied with their permissions.

Is their a way to set the default permissions of copied files from ntfs formatted disks.

---

### Post by fr34k on 2009-11-15
The permissions for a file in an Ntfs disk is -rwxrwxrwx and drwx------ for a directory

When i copy it into my Ext4 , i want this set to another default value.

---

### Post by scouser73 on 2009-11-15
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

