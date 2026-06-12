---
title: "NFS mount times out"
date: 2012-05-27
forum: General Help
---

### Post by Data Dump on 2012-05-27
I am running Ubuntu 12.04 on my laptop.  I have also setup a FreeNAS ver 8.04 server for backups.  I am trying  to do an NFS mount to the server.

I can see the mount point from the client:

bob@bob-1000HE:~$ showmount -e 192.168.90.204
Export list for 192.168.90.204:
/mnt/Dundee45 192.168.90.0

It always times out when I try to mount it

bob@bob-1000HE:~$ sudo mount -v -o tcp -t nfs 192.168.90.204:/mnt/Dundee45 /home/bob/BU
mount.nfs: timeout set for Sat May 26 09:42:54 2012
mount.nfs: trying text-based options 'tcp,vers=4,addr=192.168.90.204,clientaddr=192.168 .90.180'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying text-based options 'tcp,addr=192.168.90.204'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.90.204 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=6
mount.nfs: trying 192.168.90.204 prog 100005 vers 3 prot TCP port 896
mount.nfs: portmap query failed: RPC: Timed out
mount.nfs: mount to NFS server '192.168.90.204:/mnt/Dundee45' failed: timed out, giving up


What can I do next to troubleshoot this issue?

---

### Post by papibe on 2012-05-27
Hi Data Dump.

Could you post the content of this file on the server?
```
/etc/exports
```
Regards.

---

### Post by Data Dump on 2012-05-29
Here it is:

/mnt/Dundee45 -alldirs -mapall=nobody:nobody -network 192.168.90.0/24

---

### Post by papibe on 2012-05-29
Thanks.

I'm not familiar with those options. I failed to find them on the documentation also. How did you come up with them?

I would start with very simple options, and take it from there. Try this:
```
/mnt/Dundee45  192.168.90.0/24(rw,sync,no_root_squash)
```
Then restart nfs:
```
sudo service nfs-kernel-server restart
```
Tell us how it goes.
Regards.

---

### Post by Data Dump on 2012-05-29
The options you see in /etc/exports are setup through the GUI in FreeNAS which runs on top of FreeBSD.  I set those options up exactly like an example in the FreeNAS documention.  FreeNAS keeps the setting in it's own database and reloads them each time the server is rebooted so you cannot manually make permanent changes in that file.

When I tried your first command all I got was a syntax error.


bob@bob-1000HE:~$ /mnt/Dundee45  192.168.90.0/24(rw,sync,no_root_squash)
bash: syntax error near unexpected token `('

---

### Post by papibe on 2012-05-29
My mistake.

I apologize, those are Linux options... your server is a FreNAS (BSD based).

Change them back as they were.

Then, try this: force the use of nfsv3 instead of v4:
```
sudo mount -v -t nfs 192.168.90.204:/mnt/Dundee45 /home/bob/BU  -otcp,**vers=3**
```
Tell us how it goes.
Regards.

---

### Post by jeduffey on 2012-05-30
For what it is worth in helping you, I have been battling an issue with NFS mount timing out for many months. My server has been FreeNAS 7.2 to NAS4free 9.0.  My personal system has been from 11.04 to 12.04. I have tried many distros. I have been forced to add the "-o proto=tcp" option in order to connect to the server without a time out issue. BTW, OS X connects without options, with no fuss.

This is what I learned yesterday.

Yesterday I installed Linux Mint 9 with kernel 2.6.32-21 on an extra machine. Once I installed NFS-Common it connected to the NFS server, WITHOUT any protocol specification, in a few seconds with no problems at all.

I am now quite clear that there was in fact some major change in the LINUX kernel. Somewhere between 2.6.32 and approximately 3.0.

I am not certain if this information specifically helps your situation, but I hope that it does.

---

### Post by Data Dump on 2012-05-30
I get the same thing even when I force TCP and version 3.

```
bob@bob-1000HE:~$ sudo sudo mount -v -t nfs 192.168.90.204:/mnt/Dundee45 /home/bob/BU  -otcp,vers=3
mount.nfs: timeout set for Wed May 30 17:05:33 2012
mount.nfs: trying text-based options 'tcp,vers=3,addr=192.168.90.204'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.90.204 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=6
mount.nfs: trying 192.168.90.204 prog 100005 vers 3 prot TCP port 705
mount.nfs: portmap query failed: RPC: Timed out
mount.nfs: mount to NFS server '192.168.90.204:/mnt/Dundee45' failed: timed out, giving up

```

jeduffey - That is interesting information.  Unfortunately, I'm not getting any luck connecting no matter what.  I'm tempted to fire up a VM and try some other distros.

---

