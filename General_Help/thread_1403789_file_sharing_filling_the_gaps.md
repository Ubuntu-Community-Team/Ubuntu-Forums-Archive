---
title: "file sharing filling the gaps"
date: 2010-02-10
forum: General Help
---

### Post by adamjseed on 2010-02-10
I am relatively new to ubuntu/linux and although I have made some good progress on my server I'm struggling with a few points. I am sure what I'm about to ask has been covered in some other thread/guide but I just cant pick out the missing piece hence my direct question;

I have 2 computers; a server and mediacenter.

on the server I have installed nfs:
```
sudo apt-get install nfs-kernel-server nfs-common portmap
```
then
```
sudo vi /etc/exports
```
and added
```
/links/sharedfolder 192.168.1.1/24(rw,sync,no_subtree_check)
```

now from what I understand that will set up the share as Read Write

on the client I updated the fstab 
```
sudo vi /etc/fstab
```
and added
```
192.168.1.100:/links/sharedfolder /links/sharedfolder nfs rsize=8192,wsize=8192,timeo=14,int
```

I can now access my share on the mediacenter but it appears to be read only. Can some one point out my error.

One more question... I also sometimes don't get any content on my mediacenter in /links/sharedfolder but after a restart it picks up the share again. Any suggestions on why this happens or what to restart to pick the share up again?

Thanks in advance

---

### Post by adamjseed on 2010-02-17
bump

---

### Post by adamjseed on 2010-02-23
Ok I have done some more digging. It appears that some of my shares look to have read write capability which is strange... as I cant see what differs.

I have tried starting from the beginning...
on my server 192.168.1.100

I have a hard drive mounted in my /etc/fstab file:
/dev/sdb1 /mnt/sdb auto defaults 0 1

Next to centralise my shares I create a links folder and set up a link:
sudo ln -s /mnt/sdb/folder1 /links/folder1 &&
sudo ln -s /mnt/sdb/folder2 /links/folder2

now in /etc/exports I have
/links/folder1 192.168.1.1/24(rw,sync,no_subtree_check)
/links/folder2 192.168.1.1/24(rw,sync,no_subtree_check)   

now on my client 192.168.1.101
in /etc/fstab I have:
192.168.1.100:/links/folder1 /links/folder1 nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.100:/links/folder2 /links/folder2 nfs rsize=8192,wsize=8192,timeo=14,intr

now the weird thing is that folder1 has full read/write access where as folder2 does not.

One thing I noticed on the server when i ran:
sudo /etc/init.d/nfs-kernel-server restart

I get the following:
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: No options for /links/folder2 192.168.1.1/24: suggest 192.168.1.1/24(sync) to avoid warning
exportfs: /etc/exports [4]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1/24:/links/folder2".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


exportfs: No host name given with /links/folder2 (rw,sync,no_subtree_check), suggest *(rw,sync,no_subtree_check) to avoid warning
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ]


Can anyone point me in the right direction???

---

### Post by fepple on 2010-02-25
Can you post the output of the following?

```

ls -la /mnt
mount

```

---

### Post by adamjseed on 2010-02-25
ls -ls /mnt returns:

drwxrwxrwx 1 root root   8192 2010-01-29 22:30 sdb

i dont know if i need to but 

ls -ls /mnt/sdb retuns:

drwxrwxrwx 1 root root   8192 2010-01-27 22:15 folder1
drwxrwxrwx 1 root root  20480 2010-02-20 18:04 folder2

---

### Post by adamjseed on 2010-02-25
Well I figured it out!

The problem was in my /etc/exports

See this example:
/links/folder1 192.168.1.1/24(rw,sync,no_subtree_check)
/links/folder2 192.168.1.1/24 (rw,sync,no_subtree_check) 

I had a space in the second line

---

