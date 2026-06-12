---
title: "Problem mounting Windows partition on startup"
date: 2011-02-18
forum: General Help
---

### Post by thenyukie on 2011-02-18
I have just installed ubuntu 10.10 on my win7 laptop (Acer Timeline 3810T) with wubi.  I can mount the laptop's windows partition with no issues using NTFS Config (after installing hal), but every time after I reboot ubuntu tells me that it cannot mount the windows partition.  If I reopen NTFS config after reboot now my previously-mounted partition shows as having 0Gb of data and there is a new /host partition that represents the windows partition.  I can then mount it again by renaming it into /media/Windows and it again works until a reboot.  

I couldn't find an answer to this anywhere on the web.  Any suggestions?

---

### Post by bcbc on 2011-02-18
Wubi mounts the Windows host partition as /host. You can access it from there. Why do you want it to be /media/Windows?

---

### Post by thenyukie on 2011-02-18
Thanks for your reply.  I can't see the /host in Nautilus and I don't think it's read/write - just read only.

---

### Post by bcbc on 2011-02-18
alt-f2, 
nautilus /host

Or Places, Computer, File system, host

You should have full read/write privileges - that's standard on Wubi

---

