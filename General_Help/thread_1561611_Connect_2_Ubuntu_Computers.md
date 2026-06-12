---
title: "Connect 2 Ubuntu Computers"
date: 2010-08-26
forum: General Help
---

### Post by mtdave on 2010-08-26
Hi, I have 2 Ubuntu Computers on my home network. I haven't figured out the ways that I can connect these 2 computers to share files, remote desktop, etc. What are all my options?

Thanks

---

### Post by sikander3786 on 2010-08-26
Use [Samba]("https://help.ubuntu.com/community/SettingUpSamba") for filesharing.

Remote desktop application is already on the Applications >>> Internet list.

Post back if you get any problems setting them up.

---

### Post by rudy.elgato on 2010-08-26
I use NFS on my systems at home to mount and share filesystems between my systems.  Here's a link to some information, [http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Linux_and_UNIX_Systems](http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Linux_and_UNIX_Systems)

For remote desktops I'm using NoMachine NX Free Edition, [http://www.nomachine.com/download-package.php?Prod_Id=2069](http://www.nomachine.com/download-package.php?Prod_Id=2069).

I've played around with Samba and various flavors of vnc and eventually got them running, but were kind of a pain to setup and didn't perform anywhere near as well as using NFS and NoMachine.  For me, NFS and NoMachine NX work great and were pretty easy to setup and configure.  Run a search on NFS and NoMachine NX and you'll get alot of information about setting them up.

Good luck...

---

### Post by DeMus on 2010-08-26
> **mtdave said:**
> Hi, I have 2 Ubuntu Computers on my home network. I haven't figured out the ways that I can connect these 2 computers to share files, remote desktop, etc. What are all my options?

Thanks

I use the fstab file in /etc for sharing disks.
I share in both computers the home folder as homefolder. Then in both computers I add a folder in /media called /media/homefolder.
In fstab I write:
```
//computername/homefolder    /media/homefolder        cifs  username=guest,password=,uid=1000 ,iocharset=utf8,codepage=unicode,unicode  0  0
```
Now every time I boot the disk in the other computer is mounted and I can use it as if it was an internal disk.

---

### Post by jazzerit on 2010-08-26
you can also use sftp to share files- I find that easiest. You just need to install the package ssh on the server (or both, if your sharing files). Then, in nautilus, type sftp://username@hostname/path/to/shared/folder

---

### Post by afrowildo on 2010-08-26
How many files are you trying to share? If it's 2GB or less, the  Ubuntu One will handle that without a problem. As for remote desktop, LogMeIn have a free service ([https://secure.logmein.com/UK/](https://secure.logmein.com/UK/)) that you can use simply by installing a client on each machine and logging in. One caveat of that is that your connection is being established via their servers, though it is heavily encrypted.

---

