---
title: "Home server (maybe)"
date: 2011-03-18
forum: General Help
---

### Post by ACF1 on 2011-03-18
I have used the Ubuntu desktop software in the past and have some experience with computers but not too much (mostly just like to mess around with them on the rare occasion I have time).  Anyway, I have a new desktop with a giant harddrive.  I was thinking it would be nice to set up part of the drive as a storage device for all my media and work stuff.  I would also want to be able to access this over the internet from other computers and places.  What is the best solution to that problem? FTP? Homeserver?  Anyway, thanks for all the help.

---

### Post by papibe on 2011-03-18
For you local LAN: you just need to share the dirs where the media is. You can use [Samba]("https://help.ubuntu.com/community/Samba") or [nfs]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html"), depending what OSes are using the other machines in your LAN.

In order to access your files from the Internet, there more steps:
[LIST]
[*]Get an dynamic DNS service like [DynDNS]("http://www.dyndns.com/").
[*]Install the ddclient in your Home server.
[*]Forward the necessary port on your router to your Server.
[/LIST]
Now in order to access your files there's several options. I would stay way from ftp as in not very scure. I use rsync over ssh, but that implies that your work/college/outside machine uses linux too.

If you are going to use a windows client, I think [sftp]("http://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol") would be the safest choice. You can use the FireFTP addon for firefox, or stand alone apps like Filezilla or WinSCP. In any case:
[LIST]
[*]Install OpenSSH in your server.
[/LIST]
I hope it helps.

P.D.: there's another option: vsftpd (a more secure ftp), but I do not that very well.

---

### Post by seawolf167 on 2011-03-18
LAN access:

```
sudo apt-get install samba
```then you can browse to your machine from any other (like Windows) by typing

```
smb://ip.address.goes.here
```WAN access:

```
sudo apt-get install openssh-server
```then you can access your computer from anywhere, if you are using *nix, simply use that computer's ssh program, else you can download and use [putty]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html").

Putty has a number of versions depending on how you are trying to transfer files (secure copy, secure ftp, etc.):

[LIST]
[*]pscp
[*]psftp
[/LIST]

---

