---
title: "Sharing a USB drive on the network"
date: 2012-05-07
forum: General Help
---

### Post by aristosv on 2012-05-07
Hi,
 
I use Ubuntu 12.04
 
This is the process I use when I want to setup a file server.
 
**Install the packages**
sudo apt-get install samba samba-common
sudo apt-get install python-glade2
sudo apt-get install system-config-samba
 
**Add the users**
adduser <username>
sudo smbpasswd -a <username>
 
**Configure the share**
open samba configuration tool
Add the folder you want to share and setup the permissions access
Setup the permissions access
 
Everything seems to be working just fine.
 
The problem appears when I plug in the computer a USB drive, and I want to share that. The Samba users cannot access it. These are the same Samba users that access all the other folders on the computer without any problems.
 
What could be causing this problem, and how could I fix it?
 
Thanks

---

### Post by Morbius1 on 2012-05-07
When morbius plugs in a USB drive ( and I'm assuming it's formatted in ntfs or fat32 ) then it will mount with ownershp = morbius and permissions of 700. The only one who can access that drive is morbius.

When you create your share you can tell samba whatever you want but samba from a network perspective can either match Linux permissions or remove them but it cannot increase them.

It appears from your description that you have created a "Classic Share" so you may have an entry in smb.conf that looks something like this:
> [usb]
path = /media/smb
writeable = yes
guest ok = yes
Guest or even if you created a private share are not morbius so access is denied. The easies way to fix this is to make all remote users appear to be morbius:
> [usb]
path = /media/smb
writeable = yes
[COLOR=Blue]**force user = morbius**[/COLOR]
guest ok = yes
Then restart samba:
```
sudo service smbd restart
```

---

### Post by aristosv on 2012-05-07
The problem persists. The user can access the "NX Server" folder but not the "Unattended" folder. Any ideas?
 
```
[Unattended]
 path = /media/E030284A302829CC/Unattended
 writeable = yes
 browseable = yes
 force user = user1
```
 
```
 
[NX Server]
 path = /home/aristos/Desktop/NX Server
 writeable = yes
 browseable = yes
 valid users = user1

```

---

### Post by aristosv on 2012-05-08
It seems that mounting the USB hard disks makes them appear as local hard disks instead of USB ones. So I edited /etc/fstab with these lines (one for each usb hdd) and the sharing worked
 
/dev/sdd1 /media/usb1 ntfs uid=aristos,gid=users,umask=0000,utf8=true 0 0
/dev/sdc1 /media/usb2 ntfs uid=aristos,gid=users,umask=0000,utf8=true 0 0
/dev/sdb1 /media/usb3 ntfs uid=aristos,gid=users,umask=0000,utf8=true 0 0

---

