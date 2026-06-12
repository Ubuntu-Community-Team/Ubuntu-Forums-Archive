---
title: "Loss of 'Pictures' Folder"
date: 2012-07-31
forum: General Help
---

### Post by rogero777 on 2012-07-31
I recently noticed the total disappearance of my 'Pictures' folder on Linux Ubuntu 11.10. It is not in 'Trash', nor can it be found by the search engine in Ubuntu. 

Can anyone help me to restore it - the directory holds dozens of internet receipts as screenshots. Thanks.

---

### Post by TheFu on 2012-07-31
> **rogero777 said:**
> I recently noticed the total disappearance of my 'Pictures' folder on Linux Ubuntu 11.10. It is not in 'Trash', nor can it be found by the search engine in Ubuntu. 

Can anyone help me to restore it - the directory holds dozens of internet receipts as screenshots. Thanks.

Sure.  Find your backup tool in the menu, the one that you setup for your system right after installation to run daily or weekly. Connect your backup HDD if it isn't already connected or stored on the network or cloud. Find the latest backup, probably from last night, click your way down the file structure that matches your "*live file system*" to where the files are stored.  Right click on the the "Pictures" folder and select "**Restore**".

If you aren't using a backup tool, can I recommend 
* Deja Dup
* Back-In-Time or 
* any of these [https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities](https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities)

I've never had unexplained disappearing folders unless the HDD, cable, or controller was going bad.  

Now would be a good time to force an **fsck** and perhaps do some of the other system maintenance things needed?  [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck) will help, but the easiest way is to run it at shutdown:```
sudo shutdown -rF
```

Here's an article on Lifehacker about doing system maintenance for Linux desktops: [http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc) that you may find helpful.

Good luck with your restore!

---

### Post by unevenflow on 2012-08-05
Hey, it does not matter how you lost your data you can use PhotoRec it is part of  TestDisk for lost partitions bud you will only have to use PhotoRec its life saver

so in terminal:
[B]sudo apt-get install testdisk
[/B]

then again in terminal:
**sudo photorec**

and use this step by step guide
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
Hope that helps!

---

