---
title: "autofs(5): direct mapping NFS4 share"
date: 2011-06-25
forum: General Help
---

### Post by MacUsers on 2011-06-25
Dear all,

Last couple hrs. since the evening I'm trying to figure out how to make autofa5 work [with NFS4] using [in]direct mapping but no joy so far. So, I deiced to ask for some help here.    

Firsty, this the **"/etc/exports"** on my NFS4 server (CentOS 5.6):
```
/media/exPort           htpc(ro,sync,no_subtree_check,no_root_squash,fsid=0)
/media/exPort/mMusic    htpc(ro,sync,no_subtree_check,no_root_squash)
```and this what I have in there: 
```
[root@serv03 /]# ls -l /media/exPort/mMusic 
total 16
drwxrwxr-x 11 databank lhome 4096 Jun 23 21:25 iTunes
drwxrwxr-x  3 databank lhome 4096 Aug 19  2010 Network Trash Folder
drwxrwxr-x  3 databank lhome 4096 Aug 13  2010 Streaming Radio
drwxrwxr-x  3 databank lhome 4096 Aug 19  2010 Temporary Items
```On the client (Lucid, v10.04), 
```

root@htpc:~# cat /etc/auto.master
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
#
# mount mMusic from serv03
/-    /etc/auto.mMusic
+auto.master 
```and finally this is the **/etc/auto.mMusic**:```
root@htpc:~# cat /etc/auto.mMusic 
#!/bin/bash

nfsServ=serv03
mntOpts="-fstype=nfs4,ro,async,_netdev,rsize=32768,wsize=32768,hard,intr"

/bin/echo -n "/media/nMedia/mMusic"
/bin/echo -n -e "\t"
/bin/echo -n "${mntOpts}"
/bin/echo -n -e "\t"
/bin/echo "${nfsServ}:/mMusic"
```which is actually generate a line like:[INDENT][COLOR=Navy]*/media/nMedia/mMusic    *[/COLOR][COLOR=DarkRed][I][COLOR=Navy]-fstype=nfs4,ro,async,_netdev,rsize=32768,wsize=32768,hard,intr    serv03:/mMusic[/COLOR]
[/I][/COLOR][/INDENT][COLOR=Black]But it doesn't work - neither it throws any errors in, nor does it mount the share. All I need is to mount "*/mMusic*" (i.e. /media/exPort/mMusic) as "*serv03:/media/nMedia/mMusic*" so that tree looks like this:

[/COLOR]```
[COLOR=Black].
|-- media
|   |-- nMedia
[/COLOR][COLOR=Black]|   |    |-- mMusic
|   |    |   |-- iTunes
|   |    |   |-- Network Trash Folder
|   |    |   |-- Streaming Radio
|   |    |   `-- Temporary Items[/COLOR]
```[COLOR=DarkRed][COLOR=Black]
[/COLOR][COLOR=Black]If I mount manually, the same share mounts very nicely without any problem:
```

root@htpc:/media# mount serv03:/mMusic -t nfs4 /media/nMedia/mMusic

root@htpc:/media# mount | grep mMusic
serv03:/mMusic on /media/nMedia/mMusic type nfs4 (rw,clientaddr=10.0.11.12,addr=10.0.11.20)

root@htpc:/media# ls -l /media/nMedia/mMusic/
total 16
drwxrwxr-x 11 4294967294 4294967294 4096 2011-06-23 21:25 iTunes
drwxrwxr-x  3 4294967294 4294967294 4096 2010-08-19 20:40 Network Trash Folder
drwxrwxr-x  3 4294967294 4294967294 4096 2010-08-13 09:50 Streaming Radio
drwxrwxr-x  3 4294967294 4294967294 4096 2010-08-19 20:40 Temporary Items

```but no joy at all with autofs(5). Does anyone know if I'm missing anything here or what am I doing wrong? Any help greatly appreciated. Cheers!![/COLOR]
[/COLOR]

---

### Post by MacUsers on 2011-06-26
Sorry for rushing you guys up - I'm completely stuck here and need to get it fixed quick. Is there anyone out here been able to use autofa5 + NFS4 successfully yet? Cheers!!

---

### Post by MacUsers on 2011-06-26
:confused:  am I traveling alone on this boat?? :-k
At least, anyone can tell me where I can see the error logs for autofs?  I've already uncommented the ***LOGGING=debug*** in the "/etc/default/autofs" and then deliberately put a bug in the auto.mMusic file but nothis is being reported. No one is using autofs, at all?? Cheers!!

---

