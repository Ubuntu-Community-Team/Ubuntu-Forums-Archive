---
title: "static mount of NFS share"
date: 2010-07-29
forum: General Help
---

### Post by ackster on 2010-07-29
I'm trying to add a line to fstab to mount a share on every boot.  I can mount the share manually using

sudo mount -t nfs 192.168.2.1:/x_machine /mnt/test

I've added the line 

192.168.2.1:/x_machine  /mnt/test  nfs   rw,hard,intr 0 0

to my /etc/fstab file, but it doesn't seem to mount on boot.  What am I  missing.  I tried looking in the log files for an error, but couldn't  find anything.

Ubuntu 10.04 x64 desktop edition.

Thanks

---

### Post by mprokolo on 2010-07-29
is this what you are looking for
HowTo: Automount NTFS Drives:
[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by ackster on 2010-07-29
Not NTFS just NFS no T in there;).  Basically it a NAS box running RAID5 and formatted as EXT3.  But the share is NFS.

---

### Post by mprokolo on 2010-07-29
sorry my bad...
in any case what dmesg tells you after boot some times the network is not up when fstab tries to mount and fails
also you could try autofs

---

### Post by amauk on 2010-07-29
(I'm assuming "x_machine" is a directory on the server that you are wanting to share to client machines)

You seem to be mixing up the synatx of NFSv3 and NFSv4

NFSv3 way
```
mount -t nfs 192.168.2.1:/absolute/path/to/x_machine /local/mount/point
```

NFSv4 way
(with directory "x_machine" bind mounted within the NFSv4 root export directory)
```
mount -t nfs4 192.168.2.1:/x_machine /local/mount/point
```

---

### Post by bodhi.zazen on 2010-07-29
Although fstab works, personally I advise autofs

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

You will need to unmount the nfs share, comment out or remove the line in fstab, and configure autofs.

See the wiki pae for details.

---

### Post by ackster on 2010-07-29
Thanks autofs worked.

---

### Post by bodhi.zazen on 2010-07-30
> **ackster said:**
> Thanks autofs worked.

Glad it worked for you, IMO autofs is slick =)

---

