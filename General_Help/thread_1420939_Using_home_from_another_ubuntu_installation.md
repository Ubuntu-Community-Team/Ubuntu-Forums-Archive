---
title: "Using /home from another ubuntu installation"
date: 2010-03-03
forum: General Help
---

### Post by zuperxtreme on 2010-03-03
My previous installation got corrupted somehow(this computer isn't working very well, I get corrupted files and things often, usually causing the installation to just die), so I decided to partition the disk, resize actually. 
I gave the new resized partition 20GB for Ubuntu, and left the rest along(Around 150GB, where the /home I want is).

What I need: Make my /home the /home in the old partition. I thought about fstab, maybe making it point to the old one?

A better solution would be to grab everything in the old partition(given that it fits in the remaining 18some GB of the Ubuntu partition), format the big 150GB partition, move everything back and then set it as the new /home.

The current /home isn't necessary because this is a fresh installation(like, 10 minutes old), so what do you guys suggest?

Cheers!

---

### Post by linuxman94 on 2010-03-03
Here is a good tutorial on how to change your home directory.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by zuperxtreme on 2010-03-03
> **linuxman94 said:**
> Here is a good tutorial on how to change your home directory.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

Cheers :)

I'll try and follow it.

---

