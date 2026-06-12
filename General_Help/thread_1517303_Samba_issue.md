---
title: "Samba issue"
date: 2010-06-24
forum: General Help
---

### Post by sandsjh on 2010-06-24
Warm greetings. I have read a few threads about samba and mounting, and cannot get it straight. I welcome your assistance in helping me resolve this.

Here is basically what I have done...
sudo mkdir /media/effjsands

sudo pico /etc/fstab
//10.1.121.36/sandsjh  /media/effjsands cifs  credentials=/etc/samba/user,d_mode=777,f_mode=777 0 0

sudo pico /etc/rc.local
mount /media/effjsands

sudo pico /etc/samba/user
username=sandsjh
password=IamN0Tl33t34

I reboot and it does not mount. 

I can get Nautilus to open //10.1.121.36/sandsjh , so I know it is a valid path.


when I go to terminal and run manually, I get:
sandsjh@LTL-IT-SANDS:/etc$ ./rc.local 
mount: only root can mount //10.1.121.36/sandsjh on /media/effjsands

Regards,
Jason

---

### Post by anglican on 2010-06-25
> **sandsjh said:**
> Warm greetings. I have read a few threads about samba and mounting, and cannot get it straight. I welcome your assistance in helping me resolve this.

Here is basically what I have done...
sudo mkdir /media/effjsands

sudo pico /etc/fstab
//10.1.121.36/sandsjh  /media/effjsands cifs  credentials=/etc/samba/user,d_mode=777,f_mode=777 0 0

sudo pico /etc/rc.local
mount /media/effjsands

sudo pico /etc/samba/user
username=sandsjh
password=IamN0Tl33t34

I reboot and it does not mount. 

I can get Nautilus to open //10.1.121.36/sandsjh , so I know it is a valid path.


when I go to terminal and run manually, I get:
sandsjh@LTL-IT-SANDS:/etc$ ./rc.local 
mount: only root can mount //10.1.121.36/sandsjh on /media/effjsands

Regards,
Jason
To test a mount don't reboot, just type ```
sudo mount /media/effjsands
```... and then see what errors you get. You shouldn't need to add anything to rc.local to get it mounted at boot time. An fstab entry something like:
```
//10.1.121.36/sandsjh  /media/effjsands cifs auto,users,credentials=/etc/samba/user,d_mode=777,f_mode=777 0 0
```Should work just fine.

H

---

### Post by sandsjh on 2010-06-25
Hello. Thanks for your help.

> sandsjh@LTL-IT-SANDS:/media/effjsands/documents$ mkdir new1
mkdir: cannot create directory `new1': **Permission denied**

What is up with the permission denied error?
I did
```
sudo chown -hR sandsjh:sandsjh /media/effjsands
```

and still get the same **permission denied** error.

Thanks for anyone's assistance.

---

### Post by bodhi.zazen on 2010-06-25
The permission denied error is server side.

It appears you have mounted the share.

So on the server make sure the samba user has permissions to rw the files in question. This can be a problem in the samba server configuration or a "simple" permissions problem.

Is the server Ubuntu or Windows ?

---

### Post by sandsjh on 2010-06-25
> Is the server Ubuntu or Windows

Server 2003R2. It works fine when I login on a Windows machine. Do I have to specify my domain login somewhere? e.g. domain\sandsjh instead of sandsjh?

This Ubuntu machine is **not**joined to the domain.

Jason

---

