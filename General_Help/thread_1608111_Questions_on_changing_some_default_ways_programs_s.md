---
title: "Questions on changing some default ways programs start"
date: 2010-10-28
forum: General Help
---

### Post by vdubhack on 2010-10-28
I am running 10.10 64bit and I am wanting to change a few ways some programs start up on boot, they are as follows:
1. make NetworkManager not load on boot and require me to manually start it in the command line
2. make bluetooth not start on boot and allow to manually start it from the command line
3. make networking not boot on start and start manually from command line 


I have been trying to search on google but most of the threads I find are about removing things completely and the few that werent did not work for what I want to do. Thanks for any help with this.

---

### Post by Ichido on 2010-10-28
Try System>Preferences>Start Up Applications and Un-Check those you don't want to start. Restart to test.

---

### Post by sisco311 on 2010-10-28
> **vdubhack said:**
> I am running 10.10 64bit and I am wanting to change a few ways some programs start up on boot, they are as follows:
1. make NetworkManager not load on boot and require me to manually start it in the command line
2. make bluetooth not start on boot and allow to manually start it from the command line
3. make networking not boot on start and start manually from command line 


I have been trying to search on google but most of the threads I find are about removing things completely and the few that werent did not work for what I want to do. Thanks for any help with this.

Never tried myself, but you can try jobs-admin to enable/disable the services.

---

### Post by vdubhack on 2010-10-28
Thanks that got 2 of the 3 solved and seem to be able to bring both back up manually. But networking boots still and there was only something for NetworkManager in there and nothing about networking in general. 

Appreciate the help so far.

---

### Post by vdubhack on 2010-10-28
> **sisco311 said:**
> Never tried myself, but you can try jobs-admin to enable/disable the services.

Do I just run jobs-admin from the command line or ? I have never seen that one before.

---

### Post by sisco311 on 2010-10-28
> **vdubhack said:**
> Do I just run jobs-admin from the command line or ? I have never seen that one before.

*jobs-admin is a simple GTK+ utility that allows any administrator to easily configure jobs (services) present on their system. Jobs may be enabled and disabled, started and stopped, and can even provide tweakable settings about services.*

---

### Post by vdubhack on 2010-10-28
> **sisco311 said:**
> *jobs-admin is a simple GTK+ utility that allows any administrator to easily configure jobs (services) present on their system. Jobs may be enabled and disabled, started and stopped, and can even provide tweakable settings about services.*

Thanks installed it and seems like a really easy way to tweak a bunch of settings, Is this a new program? I havent seen anyone recommend it before. Though ran into a snag with it once I ran it, I get this error: 

No module name pkit

I am searching now to see if its needed or what the heck it even is before changing anything in jobs-admin. 

Thanks again

---

### Post by sisco311 on 2010-10-28
> **vdubhack said:**
> Thanks installed it and seems like a really easy way to tweak a bunch of settings, Is this a new program? I havent seen anyone recommend it before. Though ran into a snag with it once I ran it, I get this error: 

No module name pkit

I am searching now to see if its needed or what the heck it even is before changing anything in jobs-admin. 

Thanks again

Yep, it's a new app aimed to replace the old services-admin from [gnome-system-tools]("http://projects.gnome.org/gst/") which is not compatible with [Upstart]("http://projects.gnome.org/gst/").

---

### Post by vdubhack on 2010-10-28
Thanks again for showing about the new tool I have pretty much got it going how I want though bringing it all back up manually is not fully working but I will sort it out. Marking solved

---

