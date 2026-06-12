---
title: "Backup Windows 7 to Ubuntu?"
date: 2010-06-30
forum: General Help
---

### Post by AZDiablo on 2010-06-30
Not sure what section this post fall but....

I have a Ubuntu 9.10 server with Samba as a file server on my home network. 

I want to back up my Windows 7 computer to the Ubuntu server or Samba file server. How do I configure samba or Ubuntu to accept the backup files from windows 7.

---

### Post by mwolfe on 2010-06-30
I'm a little confused about what are you asking. Are you looking for software to do the backup to your ubuntu box? Or do you already have the software, which is say the backup utility in windows, and you simply want to automate the process of running the backup and moving the file to your samba box?
The easiest way to do that would be to mount your ubuntu/samba share in windows by right clicking on the folder and setting windows to mount that folder as a drive (forget exactly how to do this but I did it the other day and it was real simple -- previously I did it by command line but just noticed in win7 it was available via a right click menu of some sort I think).
Here is a small article about how to do it:
[http://www.groovypost.com/howto/microsoft/vista/map-a-network-drive-using-windows-vista-or-windows-server-2008/](http://www.groovypost.com/howto/microsoft/vista/map-a-network-drive-using-windows-vista-or-windows-server-2008/)

Thats not exactly how I did it, i connected to the share first then I was given some menu option where I could mount it as a drive..
Once it's mounted as a drive you can use it like any other drive, and set your backup software to save to it like any other drive.

---

### Post by AZDiablo on 2010-06-30
Let my try to clarify. 

I have a Ubuntu 9.10 server that is running Samba. The computer is setup as a file server and appears on the home network. The server appears like an external hard drive. I can manually save file to the server. (copy paste)

Windows 7 has "back up to a network drive" built into it backup software. To setup the network back up i have to browse to the location of the drive and enter a user name password. 

Windows 7 displays and error that it cannot connect to the file server. 

All the computers on the home network are windows based. they all have passwords that are required to access their stared files. The File server (samba) does not have a password. 

Do I need to configure the samba server with a password or do I have to setup a separate folder on the file server?

---

### Post by mwolfe on 2010-06-30
Yes you should probably have a password on your network share especially if you have a wireless network.. Wouldn't want someone to hack into your network and get access to all of your files if they somehow got on your wireless.
Its also possible that you don't have permissions to write to the folder you are attempting to save the backup to. You need to specify "Allow others to create and delete files in this folder" under the share options in ubuntu

---

