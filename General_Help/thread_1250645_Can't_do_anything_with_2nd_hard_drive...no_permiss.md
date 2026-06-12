---
title: "Can't do anything with 2nd hard drive...no permissions???"
date: 2009-08-26
forum: General Help
---

### Post by dtrot55 on 2009-08-26
I installed a 160gb hard drive on a PCI IDE Controller due to mobo only having 1 IDE port.  But in the beginning I wasn't able to create a share with folders because I didn't have permissions.  So I used gparted and made it a ext3 partition, and now I can't even make a folder on the drive...all i see is a lost and found folder.

Any idea on how i can get permissions back to myself so i can use this hard drive?

---

### Post by scouser73 on 2009-08-26
Go to **Terminal**, copy & paste this command:  **gksudo nautilus**

That will open Terminal as root, navigate to your new drive, **Right Click**, select the **Permissions tab** change the **Owner** drop-down menu to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write**, **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by dtrot55 on 2009-08-26
Will def give it a try...thanks

---

### Post by chriskin on 2009-08-26
you can also install the "storage device manager" and use it to change permissions (and other aspects, like mount points) of the drives you want.

---

### Post by dtrot55 on 2009-08-26
Looks like that work'd..thanks for the help everyone...what would be the terminal code or location of the storage device manager just for future reference

---

### Post by chriskin on 2009-08-27
> **dtrot55 said:**
> Looks like that work'd..thanks for the help everyone...what would be the terminal code or location of the storage device manager just for future reference

just go to add/remove and write |storage device manager| :)

---

### Post by dtrot55 on 2009-08-28
I have noticed that even when i do gksudo nautilus and set the permissions to me ... once i restart it is set back to root..any way to avoid this?  Any way i can write a boot script  or something that will mount the hard drive and give me permissions..because honestly this is getting annoying

---

