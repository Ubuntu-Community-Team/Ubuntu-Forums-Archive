---
title: "CIFS Mount Issues"
date: 2010-11-23
forum: General Help
---

### Post by peshko-lnx on 2010-11-23
(I posted this in a wrong forum). Apologies for the duplication.

Couple of things.

I use 10.10 an my server is basically Buffalo NAS.

Here is my fstab line:
//xxx.xxx.xxx.xxx/myfolder       /media/test     cifs      rw,noperm,iocharset=utf8,credentials=/etc/.smbcredentials,file_mode=0777,dir_mode=0777,users   0 0

smbcredentials contains username and password.

It mounts it successfully, but with the wrong owner. If I mount it with   root, owner of every file is root, if I mount it with user1, owner  of   every file and directory is user1.

1. It seems that it disregards .smbcredentials. If I don't specify   .smbcredentials, it asks for a pwd, but I can put any random key   combination and it would be ok and mount the remote share

2. Unmount from the user1 is impossible. Always have to umount with   root. If I try to umount with user1 I get an error that says:


user1@ubuntu10-lap:~$ mount /media/test
user1@ubuntu10-lap:~$ mount
.
.
//xxx.xxx.xxx.xxx/myfolder/ on /media/test type cifs (rw,mand,nosuid,nodev,user=user1
 
user1@ubuntu10-lap:~$ umount /media/test
umount: /media/test mount disagrees with the fstab

3. Shutdown hanging when cifs is mounted is permanent. There seems to be   no workaround. I applied MANY solutions, but seems that there is no   permanent solution.

My question is - is there a solution to any of these problems that you might be aware of?

Thanks!

---

### Post by SeijiSensei on 2010-11-23
> **peshko-lnx said:**
> 
It mounts it successfully, but with the wrong owner. If I mount it with   root, owner of every file is root, if I mount it with user1, owner  of   every file and directory is user1.

Mounting with smbmount is not really different than using smbclient. If you open a share with "smbclient -U username ..." you'll have that username's permissions.  

If the server were running Samba, you could use the "force_user" and "force_group" directives to specify a particular Unix username and password as the common owner of all the files.  I don't know how the NAS is set up though.

> It seems that it disregards .smbcredentials. If I don't specify   .smbcredentials, it asks for a pwd, but I can put any random key   combination and it would be ok and mount the remote share

I suspect the share is exported without requiring authentication and you're running as the guest user when you don't use a password.

What username owns any created files when you don't use credentials?

---

### Post by peshko-lnx on 2010-11-24
> **SeijiSensei said:**
> 

What username owns any created files when you don't use credentials?

Regardless if I use or don't use credentials, it always takes the username of the user that mounts it.

---

