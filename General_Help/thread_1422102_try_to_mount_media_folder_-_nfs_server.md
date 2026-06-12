---
title: "try to mount media folder - nfs server"
date: 2010-03-05
forum: General Help
---

### Post by redpeppery on 2010-03-05
hello fellows, first question here, please help
I try to mount /media folder from a ubuntu nfs server but I see just the mounted drives inside, but not the content of them

ex:
/media folder contains many hdd mounted on the server computer, one of them is bigbig
in exports files on server i have the following line
/media 192.168.1.1/24(rw,no_root_squash,async)
i mount this on client computer with the following command
sudo mount 192.168.1.65:/media /test
and after I can see folders from media on the server but if I try to access them the content is empty
/test/bigbig is empty

If I share the /media/bigbig folder I can see the content 
for example 
if in exports files on server i have the following line
/media/bigbig 192.168.1.1/24(rw,no_root_squash,async)
and I mount with
sudo mount 192.168.1.65:/media/bigbig /test
I can see the /bigbig mounted drive content
/test contains /media/bigbig from server 
It seems that mounted drives cannot be shared
Is it true or there is another trick
Thx

---

### Post by redpeppery on 2010-03-07
Solved, 
It seems the [I]crossmnt option in the exports file did the trick.
[/I]*nohide* This option is based on the option of the same name provided in IRIX NFS. Normally, if a server exports two filesystems one of which is mounted on the other, then the client will have to mount both filesystems explicitly to get access to them. If it just mounts the parent, it will see an empty directory at the place where the other filesystem is mounted. That filesystem is "hidden". 
Setting the *nohide* option on a filesystem causes it not to be hidden, and an appropriately authorised client will be able to move from the parent to that filesystem without noticing the change. However, some NFS clients do not cope well with this situation as, for instance, it is then possible for two files in the one apparent filesystem to have the same inode number. 
The *nohide* option is currently only effective on *single host* exports. It does not work reliably with netgroup, subnet, or wildcard exports.  
This option can be very useful in some situations, but it should be used with due care, and only after confirming that the client system copes with the situation effectively. 
The option can be explicitly disabled with *hide*. 
*crossmnt* This option is similar to *nohide* but it makes it possible for clients to move from the filesystem marked with crossmnt to exported filesystems mounted on it. Thus when a child filesystem "B" is mounted on a parent "A", setting crossmnt on "A" has the same effect as setting "nohide" on B.

---

