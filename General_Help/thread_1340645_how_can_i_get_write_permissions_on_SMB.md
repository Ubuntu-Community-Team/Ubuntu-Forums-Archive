---
title: "how can i get write permissions on SMB?"
date: 2009-11-28
forum: General Help
---

### Post by outleradam on 2009-11-28
I have this line in my /etc/fstab to enable mounting of my WRT160NL NAS.
 
//192.168.1.1/public/Video    /media/storage        CIFS    credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0
 
From what I have read, it should work, but I cannot write to the drive even after becomming root.  I can only read from the drive.  How can I enable writing to the drive?

---

### Post by efflandt on 2009-11-28
Somewhere in your comma separated list of options you need **rw** (as in read/write).  From **man mount**:

ro - Mount the file system read-only.

rw - Mount the file system read-write.

So what do think the default is on the side of safety?

---

### Post by bodhi.zazen on 2009-11-28
Your mount command looks fine, rw is not needed to rw samba shares.

It also depends on how the server is configured.

The server must allow rw and the user must have permission on the server to rw the shared directory.

---

### Post by outleradam on 2010-02-21
turns out I needed to apt-get install smbfs and set the file system as smbfs instead of cifs

//192.168.1.1/public /home/mythtv/NAS smbfs credentials=/home/adam/.smbcredentials,dir_mode=0777,file_mode=0777,uid=1000,gid=1000,rw,exec 0 0

---

