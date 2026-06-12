---
title: "cifs from fstab messing up uids"
date: 2010-01-22
forum: General Help
---

### Post by toshko3 on 2010-01-22
Hi, I am trying to mount cifs through fstab but it is not working. I have an Ubuntu samba server and a Kubuntu client. The share from the server is one dir with subdirs having different permissions and owners/groups. When I do AS ROOT:
```
smbmount //192.168.0.254/share /media/maps/share -o username=toshko%pass
```
the output of the "mount" command is as follows:
```
//192.168.0.254/share on /media/maps/share type cifs (rw,mand)
```
The result is messed up owners with different uids and groups:
```
drwxrws---  2   1001 toshko  0 2009-06-18 16:22 References
drwsrws---  6   1001   1005  0 2010-01-22 17:29 schetovodstvo
drwxrws---  4 nobody   1008  0 2009-12-21 16:58 SchetovodstvoOther
drwsrws---  2   1001 staff   0 2009-03-05 10:09 Specially for Printing

```
The same result is when I add the following to the fstab:
```
#//192.168.0.254/share /media/maps/share cifs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

```
I suppose that this is because the usernames are the same in the server and the client but the uids are different. Whatever, I don't have access to the subdirs.
When I do the above smbmount ... command with toshko user it works.
So my question is:
How do I do it in fstab?
How do I put cifs with user other than root(I gave the username manually too, instead of credentials=..., the same result)?
:confused:

---

### Post by toshko3 on 2010-01-24
Anyone???](*,)

---

### Post by toshko3 on 2010-01-26
OK, I did it - in fstab:
```
//192.168.0.254/share  /mountpoint cifs credentials=/root/.smbcredentials,uid=toshko,gid=toshko   0 0
```
Now, the BIG problem is that before any operation, the permissions of the parent directory are as follows:
```
drwxrws---  2 toshko toshko   0 2010-01-04 09:58 directory
```
and the permissions of the child file are:
```
-rwxrw----  1 toshko toshko 702 2010-01-26 11:04 toshko.xls
```
After I create a file it has the following permissions:
```
-rwxr--r--  1 toshko toshko   1 2010-01-26 11:05 test.txt
```
The question is how do I preserve the permissions, after creating a file???
I've put the "s" bit in the permissions and the "inherit permissions" option in the smb file. The problem is in the CIFS for sure, because with direct access through samba (smb://192.168.0.254/.....) it works. The strange for me is that when I save a file in OpenOffice through the map, it works and does not change the permissions, but only for already existing files, not "save as".
:confused:

---

