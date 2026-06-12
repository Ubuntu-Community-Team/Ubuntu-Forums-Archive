---
title: "can't get my permanently mounted windows share to be writable"
date: 2009-09-06
forum: General Help
---

### Post by ttguy on 2009-09-06
So I am following the advice posted at [https://help.ubuntu.com/community/MountWindowsSharesPermanently ]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")that describes how to permanently mount a Windows Share. And I can see my files but I can not write to the share.

I have smbfs installed

I have created a group called "mybook-public" with a group ID 1002 and put myself in this group using System>Admin>users and groups

I have created an empty directory under the root directory on my local system  "/public_on_mybook" where I am to mount my windows share.
This folder is owned by root and is in the group "mybook-public". The owner and group have "create and delete" files privs. Others have "access files"

My windows share is called PUBLIC and is located on my WD MyBook world edition on 192.168.5.3
The share is accessible by a user called ROGER with a password <password> 

These credentials are saved in /home/ttguy/.smbcredentials

```
username=ROGER
password=<password> 

```

/etc/fstab

now has this line in it


```
//192.168.5.3/PUBLIC   /public_on_mybook smbfs iocharset=utf8,credentials=/home/ttguy/.smbcredentials,dir_mode=0775,gid=1002 0 0
```

```

sudo mount -a 

```

causes the share to mount and I can see the files but if I go to save one it complains it does not have permissions to do so. 

If I access the same share using Connect to Server... then I can write to the share.

My original  fstab line followed the suggestion from 
[https://help.ubuntu.com/community/MountWindowsSharesPermanently#Editing%20fstab]("https://help.ubuntu.com/community/MountWindowsSharesPermanently#Editing%20fstab") here under "smbfs, group perms" where it mentions to use [FONT=monospace]"[/FONT]dmask=775" in order for the group to get write permissions. 

ie I tried

```

 //192.168.5.3/PUBLIC   /public_on_mybook smbfs iocharset=utf8,credentials=/home/ttguy/.smbcredentials,dmask=775,gid=1002 0 0

```

But if I mount with that command is in fstab I get this message
```

WARNING: 'dmask' not expressed in octal.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.

```

Hence, I tried the fstab with  dir_mode=0775 - which did not error but also did not provide write access

Any gurus have any ideas ?

---

### Post by uncle-c on 2009-09-06
[http://ubuntuforums.org/showthread.php?t=1139646](http://ubuntuforums.org/showthread.php?t=1139646)

You may find the last post in the thread of use.

I have the "noauto" in my fstab which prevents automatic mounting of my XP share at startup. Obviously you change this to "auto" if you want automatic mounting when you fire up your machine.

---

