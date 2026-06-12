---
title: "New To ubuntu"
date: 2009-09-23
forum: General Help
---

### Post by TDKING on 2009-09-23
Hey people am pretty new to ubuntu and i am looking for some help i have two hard drives installed in the computer but everytime i try to transfer a file to them its saying 


error whiles copying
The folder ......cannot be copied because you do not have permissions to create it in the destination 


why wont it let me copy anything in there or make a folder in there ? i cant even do it in the hard drive named filesystem 

so am pretty much stuck can anyone help 

Thanks 

TDK

---

### Post by scouser73 on 2009-09-23
Hi TDKING and welcome to the Ubuntu forums, please follow the instrictions below.

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by TDKING on 2009-09-23
got this when i tried 

desktop:~$ gksudo nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.



any ideas 

tbh think av installed ubuntu wrong

---

### Post by TDKING on 2009-09-23
got this as well now 


--- Hash table keys for warning below:
--> file:///root
--> file:///media/disk

(nautilus:9170): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:9170): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
ben@ben-desktop:~$

---

### Post by fragos on 2009-09-23
Samba implies network access to Windows file formats. The only Windows format I use is the FAT series. They don't support permissions as in Linux.

---

