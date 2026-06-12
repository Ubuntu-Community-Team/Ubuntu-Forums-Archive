---
title: "Windows file sharing from virtualbox?"
date: 2011-01-24
forum: General Help
---

### Post by abhilashm86 on 2011-01-24
I use VirtualBox at work, where windows7 is host and ubuntu 10.04 is guest operating system. 

I want to access my windows drives, folders in ubuntu, when i did 
sudo blkid or mount or fdisk -l, i cannot see all the drives on my machine. 

So i finally did with shared folders concept. Now i can't mount them wherever i want, but when i say automount in the virtualbox settings->sharedfolder, then it auto mounts in /media/E-drive??

But to see, copy,edit or access those media files, i need to be sudo?? With normal user i can't use those /media files.

Suggest a good method of sharing files from windows7 to ubuntu in virtualbox, since i tried all methods in vain!!

---

### Post by howefield on 2011-01-25
You could try setting the VirtualBox network adapter to bridged, and then set up a network share. (Ubuntu will appear as a separate machine on your network).

---

### Post by abhilashm86 on 2011-01-26
> **howefield said:**
> You could try setting the VirtualBox network adapter to bridged, and then set up a network share. (Ubuntu will appear as a separate machine on your network).

Thanks for reply, network share means like mounting?? can i mount windows share under /home/myname/some directory?

---

