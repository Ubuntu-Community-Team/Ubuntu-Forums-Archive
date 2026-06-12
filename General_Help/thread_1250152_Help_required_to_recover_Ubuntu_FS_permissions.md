---
title: "Help required to recover Ubuntu FS permissions"
date: 2009-08-26
forum: General Help
---

### Post by orsenthil on 2009-08-26
I made the following changes to /etc/fstab
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro,**umask=022**, 0 1

I was thinking that setting the above umask value, I can make the /host partition as 755. 
Something is really screwed up and I am unable to remove that value from /etc/fstab as well. I am getting permission denied whenever I try to edit the file. 

What should I do? 

I am using wubi.

---

### Post by danwood76 on 2009-08-26
Are you using sudo to edit the fstab file?
```

sudo gedit /etc/fstab

```

You shouldnt be able to lock the root user out of editing this file but if you have you could load up a live CD and modify it from there.
I'm really not sure the full steps with a wubi install as they dont use a partition for the main install do they?

---

### Post by The Cog on 2009-08-26
I would be inclined to boot the live/installation CD, mount the root partition from there and then edit the file.

---

### Post by orsenthil on 2009-08-26
Okay, I saved myself.
While booting, edited the kernel line
**rw init=/bin/bash **
booted into that kernel. It allowed me to edit /etc/fstab, I removed that troublesome umask value and now the problem is gone. :P

If this had not worked,
I might have tried mounting the partition as read-write or perhaps tried to use a live CD.

Thanks for the responses.

---

### Post by The Cog on 2009-08-26
> **orsenthil said:**
> Okay, I saved myself.
While booting, edited the kernel line
**rw init=/bin/bash **
booted into that kernel. It allowed me to edit /etc/fstab, I removed that troublesome umask value and now the problem is gone. I would never have thought of that trick. I must remember it. Thanks for the info.

---

