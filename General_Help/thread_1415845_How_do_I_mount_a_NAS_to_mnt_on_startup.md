---
title: "How do I mount a NAS to /mnt on startup?"
date: 2010-02-25
forum: General Help
---

### Post by switch10 on 2010-02-25
I just bought a DLink 323.  I have fun_plug installed and ssh enabled, and it works great.  

I am having trouble mounting the NAS to an actual location (i.e. /mnt/dlink)  I've added the following line to /etc/fstab

```
 //192.168.1.106/mnt/HD_a2/ /mnt/dlink smbfs username=root,password=<MY PASSWORD>,uid=1000,gid=120 0 0
```
when I run ```
 sudo mount -a
```
i get ```
 retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

The IP of the device is correct, I can get there using ssh.  I set the gid to my sambashare id number.

Any ideas?

Thanks a lot,

Dave

---

### Post by Morbius1 on 2010-02-25
Try getting rid of the "/" after :
> HD_a2[COLOR=Blue]/[/COLOR]

---

### Post by switch10 on 2010-02-25
i fixed it!  I was pointing to a directory that didn't exist:rolleyes:.  It works in SSH for some reason though...

instead of /mnt/HD_a2. I used /Volume_1

---

### Post by cjhabs on 2010-02-25
The trailing / is not the problem.
Are you able to get to the folder by using the file browser and pointing to:
smb://192.168.1.106/mnt/HD_a2

Your syntax is ok - it works here for me.

---

### Post by cjhabs on 2010-02-25
You beat me to the punch!

---

