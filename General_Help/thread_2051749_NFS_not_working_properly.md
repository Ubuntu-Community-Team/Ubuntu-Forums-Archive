---
title: "NFS not working properly"
date: 2012-09-01
forum: General Help
---

### Post by MichaelW64 on 2012-09-01
Hi all,

I'm fighting with NFS4 and can't get it to work properly.
The Server runs Ubuntu 12.04, in /etc/exports I have:
```
 /media/Pictures 192.168.1.0/255.255.255.0(sync,no_subtree_check,rw,nohide) 
```With this I can mount it on my laptop (Ubuntu 10.04) with
```
 sudo mount 192.168.1.200:/media/Pictures /mnt/SharedFiles/Pictures -o nolock 
``` but I have to type that every time I start that laptop.
If I omit the -o nolock I get ```
 mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.
 
``` and I can't get statd to run.

In /etc/fstab on the laptop I have 
```
 192.168.1.200:/media/Pictures        /mnt/SharedFiles/Pictures       nfs4 rw,user,noauto     0       0
 
```Since I use a wireless connection to hook up my laptop to the network I know that this does not work automatically.
So I type ```
 mount 192.168.1.200:/media/Pictures 
``` or ```
 mount /mnt/SharedFiles/Pictures 
``` and get ```
 No such file or directory 
```.

Adding -v to the mount command gives ```
mount.nfs4: timeout set for Sat Sep  1 23:19:01 2012
mount.nfs4: text-based options: 'clientaddr=192.168.1.13,addr=192.168.1.200'
mount.nfs4: mount(2): No such file or directory
mount.nfs4: mounting outerrim:/media/Pictures failed, reason given by server:
  No such file or directory

```The NFS share exists:
```
showmount -e 192.168.1.200
Export list for 192.168.1.200:
/media/Pictures 192.168.1.0/255.255.255.0

```and the permissions are 777 to that directory.

I've read that I should add fsid=0 to /etc/exports on the server and mount 192.168.1.200:/Pictures on the client in this case.
If I do that I don't see any files on my laptop. 

Any help is greatly appreciated.

Regards,

Michael

---

### Post by MichaelW64 on 2012-09-02
I followed this tutorial [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) and now it works. :-D
All I need now is to mount them automatically using WiFi.

Regards,

Michael

---

### Post by MichaelW64 on 2012-09-02
Got it.
In /etc/fstab I have ```
 192.168.1.200:/   /home/SharedFiles   nfs4    rw,noauto,user  0  0 
```I wrote a tiny litte bash script ```
 #!/bin/bash
# Get the shared folder via NFS

mount 192.168.1.200:/
 
```Finally I linked this script to System - Preferences - Startup Applications (Gnome Desktop) and that's it.

Regards,

Michael

---

