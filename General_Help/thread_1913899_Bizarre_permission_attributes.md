---
title: "Bizarre permission attributes"
date: 2012-01-23
forum: General Help
---

### Post by MyD0j0 on 2012-01-23
I recently moved a lot of data from a FreeNAS machine to an Ubuntu 11.10 server.  I have been trying to get the server to run [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo"), [forked-daapd]("http://macvalley.blogspot.com/2011/02/successful-installation-of-forked-daapd.html") and ushare on my network (don't remember where I got the setup help for ushare) .  Thus far, I see the ushare server on my DNLA capable devices, but none of the media; I see the forked-daapd in iTunes and Banshee, but none of the music; when connected to the NFS shares, I can see files, but cannot open them and accessing subfolders throws an error: file is of unknown type.  

After I stopped using sudo -i to make all my config changes, when I ssh into the server, this is what I see as a user and as root:

```

eric@CentralD0j0:~$ ls -al /BigDisk/MultiMedia
ls: cannot access /BigDisk/MultiMedia/..: Permission denied
ls: cannot access /BigDisk/MultiMedia/Music: Permission denied
ls: cannot access /BigDisk/MultiMedia/Pictures: Permission denied
ls: cannot access /BigDisk/MultiMedia/Movies: Permission denied
ls: cannot access /BigDisk/MultiMedia/.: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
d????????? ? ? ? ?                ? Movies
d????????? ? ? ? ?                ? Music
d????????? ? ? ? ?                ? Pictures
eric@CentralD0j0:~$ sudo ls -al /BigDisk/MultiMedia
total 52
drwxrw-r--    5 root bigdisk  4096 2012-01-18 07:56 .
drwxr-xr-x    4 root bigdisk  4096 2012-01-18 08:21 ..
drwxrw-r--    3 root bigdisk  4096 2012-01-18 21:41 Movies
drwxrw-r-- 1038 root bigdisk 36864 2012-01-06 03:54 Music
drwxrw-r--   18 root bigdisk  4096 2012-01-04 22:14 Pictures
eric@CentralD0j0:~$ 

```/etc/default/nfs-common was configured in both server and client machines as shown in the set up help:
```

NEED_IDMAPD=yes 
NEED_GSSD=no # no is default

```bigdisk is a group I created for the users of the server, of which 'eric' is a member.  What am I doing wrong with the permissions that I can't get to my files using NFS and that the ushare and forked-daapd servers aren't loading the files into their services?

Thanks!

---

