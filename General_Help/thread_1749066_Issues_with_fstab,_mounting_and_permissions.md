---
title: "Issues with fstab, mounting and permissions"
date: 2011-05-04
forum: General Help
---

### Post by Lhademmor on 2011-05-04
Hi all. I've just started using Kubuntu natty.
I had issues that Kubuntu wouldn't automatically mount my external hard drive, which was a problem since I was used to just going into a media player and start playing music, but Amarok couldn't find it if it wasn't mounted. 
So I had to add it manually in /etc/fstab using:
```

UUID=A257-7997                                  /media/Elements  vfat  defaults             0  0  

```

This led me to being able to play music in Amarok right after a boot, but I've just discovered that I'm unable to edit track details. Apparently the permissions to everything on the drive belongs to root, and other users are only allowed read and execute - not write. I can't even save new files to the drive.

I'm not very good with the whole mounting business, so my question is **how can I make my external hard drive writeable at boot?**

Thank you very much for any help :)

---

### Post by decrepit on 2011-05-04
Replace "defaults" with "rw,user"

---

### Post by Morbius1 on 2011-05-04
> UUID=A257-7997 /media/Elements  vfat  defaults             0  0If you are the only local login user take possession of the partition:
> UUID=A257-7997 /media/Elements  vfat  defaults,[COLOR=Blue]uid=1000 [/COLOR]            0  0If you have multiple login users change permissions to allow every one to access:
> UUID=A257-7997 /media/Elements  vfat  defaults,[COLOR=Blue]umask=000 [/COLOR]           0  0

---

### Post by mastablasta on 2011-05-04
funny on mine (10.10) it continuously mounts USB disk even when i unmount it it automaticly mounts it back on.

---

### Post by Lhademmor on 2011-05-05
Thanks all of you, Morbius1 your trick worked :)

---

