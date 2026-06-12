---
title: "Libra cannot open .ods file in write mode from a windows 2003 servershared folder"
date: 2012-01-20
forum: General Help
---

### Post by rsumon on 2012-01-20
Hi All,
I have mounted my Windows Server 2003 shared folder to my UBUNTU 11.04 desktop.
I can brows the files and folders. But when I am opening any file it is opening it in read only mode. I am using samba to mount my file server permanently. 

I have checked the permission in my windows server it is granted read write full access. both in sharing and in security tabs for Everyone.

I do not get any issue when i am opening the file to edit it from Windows machine.
Only getting this issue when Opening the file in Ubuntu 11.04.

Please help.

Thank you

---

### Post by dcstar on 2012-01-20
> **rsumon said:**
> Hi All,
I have mounted my Windows Server 2003 shared folder to my UBUNTU 11.04 desktop.
.........

Exactly how? If you have only mounted it RO then you will only have RO permissions.

---

### Post by rsumon on 2012-01-23
Hi dcstar,
I have added the line in my fstab as below:
//192.168.1.101/Fileserver/MediaArchiv    /media/fileserver smbfs  username=rsumon,password=nomusr,uid=marx,gid=marx 0 0 

Thats what I have got in the forum to include in my fstab for full access. I have checked my WIN server 2003 shared folder security and sharing options as well. both of them has read write permission granted. Please help.

Thank you.
Razibul

---

