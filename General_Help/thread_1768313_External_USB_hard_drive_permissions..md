---
title: "External USB hard drive permissions."
date: 2011-05-26
forum: General Help
---

### Post by Silvernail on 2011-05-26
I have a Seagate 1.5 terabyte external USB hard drive that stays permanently attached to my desktop computer. The icon shows up on the desktop screen.

All directories have only the superuser permissions set. All other files are set to 777 permissions. Reading the permissions tab from the desktop icon popup window says 'permissions can not be determined'.

'chmod' is not effective even though -v reports that it is.

How do I correct this problem?

TIA
Dave

---

### Post by Silvernail on 2011-06-23
Has no one ever encountered this problem?

---

### Post by wildmanne39 on 2011-06-23
> **Silvernail said:**
> I have a Seagate 1.5 terabyte external USB hard drive that stays permanently attached to my desktop computer. The icon shows up on the desktop screen.

All directories have only the superuser permissions set. All other files are set to 777 permissions. Reading the permissions tab from the desktop icon popup window says 'permissions can not be determined'.

'chmod' is not effective even though -v reports that it is.

How do I correct this problem?

TIA
Dave
Hi try this command.
```
sudo chown -R username:username /media/usbdrive

```
this will work if your drives partitions is a linux partition.
the /media/usbdrive is your drive, and it will be in this format not as sda.

---

### Post by life in color on 2011-06-23
What type of hard drive is it? Like is it ntfs or FAT(Windows) ext2 or ext3(Linux) HFS+(I'm pretty sure that's MAC)?

---

### Post by derklempner on 2011-06-23
For all my network shares and external drives that are "permanently attached", I just create a root-level directory and mount them via **fstab** when the computer boots.  For example, I'd create a directory named **/ext_tb_hd** and make sure that the directory is owned by my account.  Then **fstab** mounts the drive thusly:

```
/media/EXTERNAL_STORAGE	/ext_tb_hd	cifs	guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777	0 0
```
(Remember that this is just my example of an **fstab** entry; depending on your hard drive's file system, volume name, etc., you will need to make changes to the above.)

If all permissions and ownership for the directory **/ext_tb_hd** are set properly, then problem solved.

---

