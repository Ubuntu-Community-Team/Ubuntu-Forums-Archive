---
title: "I'm unable to change group and ownership of folder"
date: 2010-01-08
forum: General Help
---

### Post by marklodge on 2010-01-08
hi all..
i just added a seagate freeagen external drive, i'm running Debian Lenny.i can access all files on the drive, but the owner and group is set to root, and i cannot change it to another user.
I need to change the user and group of a folder videocache to squid:squid, i tried ```
 # chown -R squid:squid videocache

```
but the owner and group does not change
please tell me how to force the permissions to chane

Thank you in advance

---

### Post by scouser73 on 2010-01-08
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by Leppie on 2010-01-08
as you are operating from a root shell (at least the # you put there should represent the root shell), the only thing i could think of is that this partition is something like ntfs, is that right? ntfs folder permissions are difficult to handle in linux.

if this wasn't in a root shell (a normal shell prompt shows $ not #), change to root shell using the "su" command.

---

### Post by bodhi.zazen on 2010-01-08
> **Leppie said:**
> if this wasn't in a root shell (a normal shell prompt shows $ not #), change to root shell using the "su" command.

Ubuntu uses sudo, so sudo -i

:lolflag:

@ Leppie : if this is a system file, you should not need to change permissions, and changing permissions of system files can result if security holes or system failure.

What are you trying to do exactly ?

---

### Post by Leppie on 2010-01-08
> **bodhi.zazen said:**
> Ubuntu uses sudo, so sudo -i

:lolflag:

@ Leppie : if this is a system file, you should not need to change permissions, and changing permissions of system files can result if security holes or system failure.

What are you trying to do exactly ?

the OP is using Debian Lenny, **_not_** Ubuntu:
> **marklodge said:**
> i just added a seagate freeagen external drive, **_i'm running Debian Lenny_**.

---

### Post by marklodge on 2010-01-08
hi
thanks for the reply guys
i tried all of the above
but in nautilus...when i select squid it just bounces back to root
and i tried the other method too
is there a way i can change the filesystem? without losing data?

---

### Post by Leppie on 2010-01-08
what is the current filesystem of that partition?
you can check that with blkid:
```
#blkid
```
or if you are using ubuntu:
```
sudo blkid
```

---

### Post by marklodge on 2010-01-08
hi heres the result
```

/dev/sda1: UUID="9db54eca-9b23-4c91-b610-e3a46aa796b8" TYPE="ext3" 
/dev/sda5: TYPE="swap" 
/dev/sdb1: UUID="886CF1476CF13114" LABEL="FreeAgentDrive" TYPE="ntfs" 

```

i was thinking if i could create anohter partition and format is with the ext3 filesys if i cant get this to work
thanks

---

### Post by Leppie on 2010-01-08
just as i thought, the freeagent drive is formatted ntfs.

if you have enough free space on the drive left, you could resize the ntfs partition, create an ext3 partition, copy everything over to the newly created ext3 partition, then remove the ntfs partition and then resize the ext3 partition to occupy the whole disk.
you can use gparted with ntfsprogs to do this:
```
#apt-get install gparted ntfsprogs
#gparted
```

---

### Post by marklodge on 2010-01-09
thank you Leppie..im doing that now, its a terabyte drive, and i'm running vidoecahce. and before i bought the terabyte drive i just had a 80gig and it wwas full of videos already..
Regards

---

### Post by Leppie on 2010-01-09
if you only use it on  linux systems, you could also try reiserfs, xfs and ext4 (these filesystems work very well with large files).

---

### Post by HiImTye on 2010-01-09
you should set the owner when you mount it if it is a filesystem that doesn't store ownership data under linux
then you have to change the owner of the mount point

---

