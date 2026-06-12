---
title: "Bulk rename files over network by mount?"
date: 2012-02-12
forum: General Help
---

### Post by Red Kelly on 2012-02-12
Is it possible to bulk rename files on my NAS from my laptop?
Server is running Ubuntu 10.04LTS and laptop 10.10. 

Could I mount the partition locally then use a standard renaming app? 
I have tried this but I cant work out how to mount it.
```
sudo mount -t cifs //SERVER/media/MEDIA/Temp -o username=luke-server,password=****** /mnt/Temp

```

I get this reply
```
mount: wrong fs type, bad option, bad superblock on //SERVER/media/MEDIA/Temp,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The server partition is ntfs
the server name SERVER
server IP 192.168.1.10
username on server luke-server
location of dir I wont to mount /media/MEDIA/Temp
The server's /media/MEDIA dir is samba shared

Am I heading in the right direction? Or is there an easier way to do this? An app that works over network?

---

### Post by Red Kelly on 2012-02-12
Sorry realized I was trying to mount an nfs without installing nfs
This website made it easy, :)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

