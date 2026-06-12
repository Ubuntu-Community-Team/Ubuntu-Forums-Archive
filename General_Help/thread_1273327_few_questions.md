---
title: "few questions"
date: 2009-09-23
forum: General Help
---

### Post by mimoza on 2009-09-23
is it possible to make one of the users "root"? or you can be root only trough the "sudo -i" in terminal?

and i have a problem... I am not privileged to access some folders. because I'm not the owner. owner is root.
question is... how to change it?

thanks for answers in advance.

---

### Post by Bachstelze on 2009-09-23
> **mimoza said:**
> is it possible to make one of the users "root"? or you can be root only trough the "sudo -i" in terminal?

Technically possible but definitely not recommended for normal use.

> **mimoza said:**
> and i have a problem... I am not privileged to access some folders. because I'm not the owner. owner is root.
question is... how to change it?

What are the folders in question?

---

### Post by mimoza on 2009-09-23
folders are on my 2nd, slave drive.

---

### Post by mimoza on 2009-09-23
folder's location is "/media/HD2/"

---

### Post by Bachstelze on 2009-09-23
If it's a Windows (FAT32 or NTFS) drive, see [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

If it's formatted in a filesystem that supports UNIX permissions, just use chown and chmod, there is plenty of doc available about it.

---

### Post by scouser73 on 2009-09-23
> **mimoza said:**
> is it possible to make one of the users "root"? or you can be root only trough the "sudo -i" in terminal?

and i have a problem... I am not privileged to access some folders. because I'm not the owner. owner is root.
question is... how to change it?

thanks for answers in advance.

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by mimoza on 2009-09-23
> **Bachstelze said:**
> If it's formatted in a filesystem that supports UNIX permissions, just use chown and chmod, there is plenty of doc available about it.

it is. and... uh... little more help? I'm quite new to ubuntu and terminal, so it is a little problem for me to figure this out.

---

### Post by lightstream on 2009-09-23
> **mimoza said:**
> it is. and... uh... little more help? I'm quite new to ubuntu and terminal, so it is a little problem for me to figure this out.

**chown myusername:myusername filepath/filename**

The above changes the ownership. You shouldn't then need to use chmod, which sets what actions are permitted (read, write, execute).

---

### Post by mimoza on 2009-09-23
oh! it works! :D

thanks so much. everybody. :)

---

