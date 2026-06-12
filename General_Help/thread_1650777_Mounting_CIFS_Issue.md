---
title: "Mounting CIFS Issue"
date: 2010-12-22
forum: General Help
---

### Post by slice16 on 2010-12-22
Morning All,

I am having a strange issue with mounting my NAS using the mount command as well as /etc/fstab.

My fstab is as follows:

```
//192.168.1.2/MEDIA /home/paul/media cifs defaults,credential=/root/.credentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

My Credential file has 0700 and looks like:

```
username=username
password=password
```

When I mount the drive, I can write to the top level (MEDIA), but I dont have any write access below. I can if I sudo.

I can mount the drive using smbclient using the above credentials and it works fine. 

Any ideas?

Thanks.

Paul

---

### Post by slice16 on 2010-12-22
Just an update, when I do:

```
sudo mount -a -v 
```

I get the following error;

```
Credential formatted incorrectly: (null)

```

This would make me believe the credential file specified is at fault.

---

### Post by slice16 on 2010-12-22
Sorted :) turns out I needed to add noperm as an option.

found the answer here:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

