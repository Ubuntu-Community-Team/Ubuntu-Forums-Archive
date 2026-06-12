---
title: "Nautilus demands to be in root to open"
date: 2011-07-12
forum: General Help
---

### Post by mbossanova on 2011-07-12
Hello everyone, I have had this problem with 10.04 for a long while now. Whenever I try to open a folder or a program tries to launch one, a prompt comes up for 
                          persmission to open 'nautilus '/path/to/folder/" asking for my password. It raises privilege and forces me to browse nautilus as root. Really annoying to have to put 
                          in the pass everytime I just want to browse/open a folder and I dont' want to be going into root like this all the time. Is this a problem with Nautilus itself or 
                          what, and how can I fix this?

---

### Post by DawieS on 2011-07-12
Welcome to the forums!:smile:

You have probably formatted your data partition using **Gparted**, with **root** now being the owner of the partition. To rectify that, open a terminal and type:
```
sudo nautilus
```This will open a file browser owned by **root**. Click on the data drive/partition to mount it, then right-click on the drive icon and select **Properties** then **Permissions**.

I recommend that you change both the **Owner** and **Group** to your user name, with **Create and delete files** at **Folder access**, and **---** at **File access**. At **Others** you may select **Access files** with **---** at **File access**, or whatever permissions you may deem appropriate.

Click on **Apply Permissions to Enclosed Files** and close the file browser and terminal.

---

