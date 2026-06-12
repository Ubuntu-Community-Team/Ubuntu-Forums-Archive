---
title: "Network Two Computer Together?"
date: 2011-03-31
forum: General Help
---

### Post by galacticaboy on 2011-03-31
I want to network 2 computers together. We are hooked up to the same internet router. I have Xubuntu 10.04, and he has Windows 7. Our computers are right next to each other. I can do it in Windows, but I need to know how to do it in Xubuntu. We are going to share files with it and play games together. Help!
David

By the way, I only have one NIC card and he only has one NIC card. We are hoping to not spend any money doing this...

---

### Post by 3Miro on 2011-03-31
I don't know about games, you will need a game that supports this thing and then it should be enough to just have the machines connected to the same router. I have done this with Diablo II and two computers on my router.

For sharing files, you want to take a look at Sambe or NFS. 

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I think NFS is easier to setup and it is surely more stable, although Samba is the method of choice in a mixed Windows/Linux environment. (you can connect from Windows 7 to a NFS or Samba).

---

### Post by Thund3rstruck on 2011-03-31
NFS is only for Unix-to-Unix talk; Windows 7 can only talk to NFS if you have the Ultimate Enterprise license. 

The best thing to do is do decide which one of those machines is going to share files. If it's Windows then use Computer Manager (start > run > compmgmt.msc) to create a file share. If it's Linux then you have to install samba (smbfs) and configure it. 

Either way you'll want to create accounts on both machines with the same username and password. 

```

Windows to Linux Connection: start > run > \\remoteIpAddress\ShareName
Linux to Windows Connection: $ sudo mount.cifs //remoteIpAddress/ShareName /path/to/mount -o username=WindowsUserName,rw,uid=LinuxUserName

```

---

