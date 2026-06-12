---
title: "How to start samba service at boot up ?"
date: 2010-01-20
forum: General Help
---

### Post by chupalo on 2010-01-20
I'm aware that a similar thread was posted a few years ago but I've searched the forum and tried out a few proposed solutions and am still unable to get Samba to start up correctly upon boot up.

I have just installed Ubuntu 9.10 and am a brand new user so I'm learning as I go.  I've also seen that this is a recognized bug and a fix has been released but I cannot tell how or if this has been automatically integrated via the Update Manager or not.

Either way I am still manually starting Samba each time I boot up.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/462169](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/462169)

Can someone please give me hand in making this correction?

Thank you in advance for any and all help.

FJ

---

### Post by wojox on 2010-01-20
Try 

```
sudo gedit /etc/rc.local
```

then add the line 

```
/etc/init.d/samba restart
```

just above where it says exit 0

---

### Post by chupalo on 2010-01-20
Fantastic!  That was easy and worked!

Is there a quick explanation about this rc.local file?  Where can I read up on its functionality?

Thanks a lot for your help.

---

