---
title: "mount system call is failing."
date: 2009-08-28
forum: General Help
---

### Post by paldebojyoti on 2009-08-28
Hi,

I am facing problem while using mount() system call in my ubuntu 8.10 PC. Within my application, I am calling the mount call to mount a USB device to a specific directory, like this:
   mount("/dev/sdb", "/media/myusb/",  "ext3", MS_RDONLY, 0))
But every time I am getting the errors either "EBUSY" or "EINVAL". I changed the mount flag options also, but the error remains.
Instead if I use this command line option "mount /dev/sdb /media/myusb/", it works fine.

Could you please tell me what error I have made? Any help is appreciated.

Regards,
Deb

---

### Post by scouser73 on 2009-08-28
Please follow the instructions set out in this tutorial:[[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by kjohri on 2009-08-28
Mount the USB manually. Then execute the mount command from shell. It will list all the mounted drives. Please the information given for the USB drive. Now using the parameters listed in the mount output, give parameters to the mount system call. For example in my case, I got the following output from mount command:

/dev/sdb1 on /media/PKBACK# 002 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

So in my case it could be,

mount ("/dev/sdb1", "/media/PKBACK# 002", "vfat", MS_RDONLY, 0);

Also, it might already be mounted before you run the program. So unmount and then run the program.

---

