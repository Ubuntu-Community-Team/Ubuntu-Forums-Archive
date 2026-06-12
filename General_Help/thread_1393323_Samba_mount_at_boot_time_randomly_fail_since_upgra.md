---
title: "Samba mount at boot time randomly fail since upgrade to 9.10"
date: 2010-01-29
forum: General Help
---

### Post by mansonthomas on 2010-01-29
Hi,

  I've a server at home which run samba.

  On my computer, I mount at boot time through the /etc/fstab some shares. 

  I was working flawlessly on 9.04 and previous version.

  Since 9.10 version, it sometime fails to mount the share and I need to run 

[PHP]sudo mount -a[/PHP]

to get my mount shared mounted. (the command "mount -a" always work).

  Any idea of what's going wrong on 9.10 ?


Regards,
Thomas.

---

### Post by Morbius1 on 2010-01-29
It's possible that the line in fstab is being executed before the network connection is actually up. Try adding the following option to your fstab declaration for that remote share: 

**_netdev**

[COLOR=Blue]*Don't forget the leading "_"*[/COLOR]

From man mount:
> The filesystem resides on a device that requires network access (used to prevent the system from attempting to mount these filesystems until the network has been enabled on the system). 

---

### Post by mansonthomas on 2010-01-29
Thanks Moribius1,

I'll try that tonight.

Regards,
Thomas.

---

### Post by stevanbt on 2010-01-29
Hi,
I had a similar problem a while back and if I remember correctly /etc/fstab is accessed before the network interface is up and running.  Therefore, at boot time the samba share cannot be found.

The following is all from memory (which is not as good as it should be)...

To get round this I put an entry in /etc/rc.local to run 
```
mount -a
```

Then later I discovered the wonders of [autofs]("https://help.ubuntu.com/community/Autofs")... and it works like a dream.

Hope this helps.

Thanks, Steve.

---

