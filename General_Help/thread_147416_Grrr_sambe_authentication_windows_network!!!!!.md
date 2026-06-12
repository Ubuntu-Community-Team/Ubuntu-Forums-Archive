---
title: "Grrr sambe authentication windows network!!!!!"
date: 2006-03-20
forum: General Help
---

### Post by donnysrx on 2006-03-20
hi all

bloody passwords

When i click on network servers on my breezy box to access my windows network places(shareddocs), i get asked for authentication and a Password that I have no idea what it is, (I've done some updates,never used to ask me for a password or anything,just worked)

and vicea versa when i click on the SMB shared folder from my windows PC I get asked for a password.

I cant fine any mention of setting a password anywhere.

help pls, before I start burning disks, its easier.:-k

---

### Post by timas on 2006-03-20
The password/login for your Windows machine is likely to be "guest" with either no password, or "guest" as password.

The password for your SMB shared folder is one of the users that has access to that folder on the machine itself.. the owner of the folder perhaps?

---

### Post by donnysrx on 2006-03-20
ok followed this;......[http://easylinux.info/wiki/Ubuntu#Samba_Server](http://easylinux.info/wiki/Ubuntu#Samba_Server)



I didnt have smbfs installed,I followed the instructions read/write folder sharing.

when you logging in from either windows or the SMB server PC you use your user 'network_name' you set in smb.conf file and of course the password, ...what fun, i used to like windows, it had no security,lol:mrgreen:

---

### Post by Ranime on 2006-03-20
Hi, I had the exact same problem. You can solve this problem by mounting your network shared windows folder:

First I got the Samba File System:
```
sudo apt-get install smbfs
```

than I followed the guide on how to auto-mount remote filesystems:
[http://www.ubuntuguide.org/#automountnetworkfoldersall]("http://www.ubuntuguide.org/#automountnetworkfoldersall")

Read the howto with care and to the letter! Change the variables (IP's, foldernames, etc) to YOUR specs, and you should be fine!

Let me know if it worked out ;)

---

### Post by mr.p on 2006-03-20
[QUOTE=donnysrx]hi all

bloody passwords

When i click on network servers on my breezy box to access my windows network places(shareddocs), i get asked for authentication and a Password that I have no idea what it is, (I've done some updates,never used to ask me for a password or anything,just worked)

and vicea versa when i click on the SMB shared folder from my windows PC I get asked for a password.

I cant fine any mention of setting a password anywhere.

help pls, before I start burning disks, its easier.:-k[/QUOTE]
[http://www.ubuntuforums.org/showthread.php?t=147210](http://www.ubuntuforums.org/showthread.php?t=147210)

I have posted my way of using Nautilus to access SMB shares in the above thread.

---

