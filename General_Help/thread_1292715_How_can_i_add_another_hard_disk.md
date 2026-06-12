---
title: "How can i add another hard disk?"
date: 2009-10-16
forum: General Help
---

### Post by stirredo on 2009-10-16
Hi everyone,

I am a complete newbie to ubuntu.

I installed it after i couldn't install windows xp on my pc and got frustrated.:P

So any way I want to add another disk to my PC. I have successfully installed gparted and I can see my second hard disk in the Gparted>Devices menu. Apparently i am supposed to mount it or something. 

Could you please tell me step by step as i don't know a single thing about ubuntu.

i am using ubuntu 9.04 jaunty.

Also: could you please refer me a good getting started guide for ubuntu. I have seen the getting started guide in the top menu bar, it starts with telling me what a mouse pointer is. I am not that much of a noob. I am somewhat of a power user of windows. Please refer me something of that level.

EDIT: guide by justleen worked....thanks
**One more question: How am i supposed to let myself read/write files on it. Also, is there a permanent way of making my normal username use the privileges of root user. I dont want to enter password each and everytime.**

---

### Post by justleen on 2009-10-16
You will have to add the disk to /etc/fstab if you want it to be automaticly mounted.
If you see the disk in gparted you should know now which device it is (/dev/sdb1 for example)
To find the UUID for that device, do ```
 ls -la /dev/disk/by-uuid/ |grep sdb1 
``` that will give you a string like  "0007543e-eec8-46f8-bfeb-495f6f441a06"

Copy that string.

open up fstab
```
 sudo gedit /etc/fstab 
```

add a line 
```

UUID=0007543e-eec8-46f8-bfeb-495f6f441a06 /media/new_disk    ext4    relatime        0       2 
```
where /media/new_disk is the mountpoint for the disk. If you formatted the disk to something else then ext4, change that to the correct value too.
Save and close the file.
Final thing: create the mountpoint ```
 sudo mkdir -p /media/new_disk 
```
If all is well, you should be able to mount is now with ```
 sudo mount -a
```

---

### Post by sisco311 on 2009-10-16
> **stirredo said:**
> 
Also: could you please refer me a good getting started guide for ubuntu. I have seen the getting started guide in the top menu bar, it starts with telling me what a mouse pointer is. I am not that much of a noob. I am somewhat of a power user of windows. Please refer me something of that level.

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

Ubuntu Pocket Guide and Reference (link in my signature)

[http://www.ubuntugeek.com/]("http://www.ubuntugeek.com/")

[https://help.ubuntu.com/]("https://help.ubuntu.com/")

---

### Post by stirredo on 2009-10-16
> **justleen said:**
> You will have to add the disk to /etc/fstab if you want it to be automaticly mounted.
If you see the disk in gparted you should know now which device it is (/dev/sdb1 for example)
To find the UUID for that device, do ```
 ls -la /dev/disk/by-uuid/ |grep sdb1 
``` that will give you a string like  "0007543e-eec8-46f8-bfeb-495f6f441a06"

Copy that string.

open up fstab
```
 sudo gedit /etc/fstab 
```add a line 
```

UUID=0007543e-eec8-46f8-bfeb-495f6f441a06 /media/new_disk    ext4    relatime        0       2 
```where /media/new_disk is the mountpoint for the disk. If you formatted the disk to something else then ext4, change that to the correct value too.
Save and close the file.
Final thing: create the mountpoint ```
 sudo mkdir -p /media/new_disk 
```If all is well, you should be able to mount is now with ```
 sudo mount -a
```

Thanks it works!

> **sisco311 said:**
> [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Ubuntu Pocket Guide and Reference (link in my signature)

[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

[https://help.ubuntu.com/](https://help.ubuntu.com/)
Thanks for the links....i am gonna read them now.

---

### Post by scouser73 on 2009-10-16
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by justleen on 2009-10-16
> **scouser73 said:**
> Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

.. which doenst even mention fstab... ?

---

