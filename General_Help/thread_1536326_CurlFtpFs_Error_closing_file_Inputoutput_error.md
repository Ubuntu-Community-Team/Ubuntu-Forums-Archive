---
title: "CurlFtpFs: Error closing file: Input/output error"
date: 2010-07-22
forum: General Help
---

### Post by cj.surrusco on 2010-07-22
I have a drive in my home FTP server mounted at /media/Data using curlftpfs in my /etc/fstab.
```
curlftpfs#ftp://cj:*password*@192.168.1.101/media/Data /media/Data fuse _netdev,allow_other,uid=1000,gid=1000,umask=0022 0 0
```

It appears to mount correctly on boot, and I haven't had any problems reading files. However, when I try to copy a file over using Nautilus, it will do almost all of the process and then stop close to the end with this error: 

> There was an error copying the file into /media/Data/Documents.
Error closing file: Input/output error

I am using the newest version of curlftpfs.

Any help would be greatly appreciated.

Thanks.

---

### Post by JanMalte on 2010-08-03
It seems like curlftpfs 0.9.2 has some problems. Take a look at this [Launchpad Entry](https://bugs.launchpad.net/ubuntu/+source/curlftpfs/+bug/120018). It seems like downgrading works for most people.

---

### Post by cj.surrusco on 2010-08-03
Thanks for the suggestion, but I already tried downgrading and had the same problem. I've switched over to sftp now instead, and I haven't had any problems yet.

---

### Post by jaya28inside on 2010-12-02
haaah??? Is that for a real?

My case was posted on this thread link
```
http://ubuntuforums.org/showthread.php?p=10188927#post10188927
```

I tot now I need to switch to sftp like u said.

great thanks!

---

### Post by BigHui on 2011-01-22
See solution trouble in [https://bugzilla.redhat.com/show_bug.cgi?id=671204](https://bugzilla.redhat.com/show_bug.cgi?id=671204)

---

