---
title: "Mounting a CIFS share in read/write"
date: 2011-03-24
forum: General Help
---

### Post by herculec on 2011-03-24
Hi,  I have a Samba share running on one ubuntu server, and I am trying to mount it from another ubuntu server using the mount -t cifs command.  I can successfully connect to the share but I cannot write to it when I connect using the mount command. If I use smbclient then I can write to it, so I do not think it is a problem with the share itself.  I use the following command line with mount (and many variations)```
 mount -t cifs //server/w /media/w -o guest
```   I get a permission denied message if I try and write to it.  If I use the following: ```
smbclient //server/w -o guest
```  it works fine!
Any suggestions to get mount working?  
Thanks.  

Samba configuraion is as follows:```
 workgroup = EXAMPLE
security = user

[w]   
path = /data/w
browsable = yes
guest ok = yes
read only = no
create mask = 0755

```

---

### Post by blind2314 on 2011-03-24
To your samba config, add```
writeable = yes
```
 
If that doesn't work, also try this.
 
```
mount -t cifs //server/w /media/w -o rw,guest
```

---

### Post by herculec on 2011-03-24
Thanks blind - didn't work though!

I suspect that the writeable=yes is not necessary, because the share works using smbclient and also via windows clients.

Any other ideas?

---

### Post by blind2314 on 2011-03-24
Do an ```
ls -l
``` for the actual directory that you're trying to share out and post the results.

---

### Post by herculec on 2011-03-24
```
ls -l /data
drwxr-xr-x 8 nobody nogroup  4096 2009-11-29 22:08 w
```

---

### Post by blind2314 on 2011-03-24
```
cd /data
sudo chown <yourUser>:<whateverGroupYouWant> w

```
 
After that, try the mount command and see if you can write.

---

### Post by herculec on 2011-03-24
Hi blind,

Is there a way of fixing the problem without breaking the share for my other clients? The setup of the share was taken directly from the Ubuntu manual and has been working without any problems from windows clients and also from Ubuntu using the smbclient program.

---

