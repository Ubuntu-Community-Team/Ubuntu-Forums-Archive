---
title: "NTFS to Ext4 permission and automount problem"
date: 2010-03-02
forum: General Help
---

### Post by 8301 on 2010-03-02
I have converted 5 drives from ntfs to ext4 and thrown out windows completely. Now Iam using 9.10

Now to the problem 
When using samba but my laptop cant open shared directory subfolders in the recently converted htpc. But the htpc can do it on the laptops samba share. 
Ive discovered that the folder and file permissions isn't the same on the htpc compared to the laptop.

ex.

HTPC Folder on /home/htpc/

Owner htpc
Folder access: Create and delete files
File access: ---

Group htpc
Folder access: None
File access: ---

Others
Folder access: none
File access: ---

Execute a box with a - in it

On the laptop

Owner laptop
Folder access: Create and delete files
File access: ---

Group laptop
Folder access: Access files
File access: ---

Others
Folder access: Access files
File access: ---

Execute empty box

How can I change the permissions on 4.1 terrabyte of folders and data files?

---

### Post by 8301 on 2010-03-02
Solved

Used this guide

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

