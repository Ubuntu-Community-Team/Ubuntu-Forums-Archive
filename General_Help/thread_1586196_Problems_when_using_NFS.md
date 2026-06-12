---
title: "Problems when using NFS"
date: 2010-10-01
forum: General Help
---

### Post by tgcUbuntu on 2010-10-01
I have two computers with Ubuntu 10.10 running and I am trying to share a folder using NFS version 3. On the server I have these packages installed: nfs-kernel-server and nfs-common
and on the other computer I have: nfs-common

I can get the folder shared across on the 2nd computer but when I do a "ls -l" I get bad uid and gid's:
-rw-r--r-- 1 4294967294 4294967294    15 2010-09-30 20:15 test.txt
All the files have these same numbers for the uid & gid.

Here is my /etc/exports file:
/home/user	10.11.15.0/255.255.255.0(rw,sync,no_subtree_check)

And here is the entry in /etc/fstab on the second computer:
10.11.15.1:/home/user /home/user nfs users,exec,auto,rw 0 0

When I do the command: rpcinfo -p on the 1st computer I get this:
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  60409  status
    100024    1   tcp  37605  status
    100021    1   udp  41695  nlockmgr
    100021    3   udp  41695  nlockmgr
    100021    4   udp  41695  nlockmgr
    100021    1   tcp  39767  nlockmgr
    100021    3   tcp  39767  nlockmgr
    100021    4   tcp  39767  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100005    1   udp  37282  mountd
    100005    1   tcp  45444  mountd
    100005    2   udp  37282  mountd
    100005    2   tcp  45444  mountd
    100005    3   udp  37282  mountd
    100005    3   tcp  45444  mountd

which seems to indicate that NFS version 4 is also running. I am trying to use version 3.

So does anybody know what is causing the messed up uid/gid problems? And also is there anyway is explicitly indicate that I want NFS ver. 3 to be used?

---

### Post by SeijiSensei on 2010-10-01
Try adding "mountvers=3" to the list of characteristics in /etc/exports.  I believe that will force the server to use NFS3 and tell the client to use it as well. See "man nfs" for details.

---

### Post by luvshines on 2010-10-01
Can you do this ??

cat /etc/passwd | grep 4294967294

on the server. Also ls -l for the /home/user on server

I think the file on server that was created is being owned by nfsnobody on the client

On the client since nfsnobody user is not recognized, UID/GID are shown as it is

---

### Post by tgcUbuntu on 2010-10-06
Thanks for the help. I added the "mountvers=3" option to the /etc/fstab file for the shared folder on the non-server machine and that fixed the user/group id problems.

I ended up with another problem. When rebooting the 2nd computer the nfs shared folder didn't mount. I could manually mount it and all the files were there with the right user/group id's. I'm not sure what was causing this. But in the meantime when copying one drive to another I managed to overwrite the wrong drive so now I have to reinstall Ubuntu.

---

