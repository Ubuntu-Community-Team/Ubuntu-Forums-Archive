---
title: "Windows 7 needs to login to Samba share"
date: 2012-07-04
forum: General Help
---

### Post by DingusFett on 2012-07-04
Hi everyone, I have a HTPC running Xubuntu 11.10 that has a Samba share so my fiance can send files directly from her Windows 7 laptop to the HTPC. The problem is tonight it keeps coming up asking for a login, which has not happened previously. Also, from my desktop running Precise, I can get to it fine without any login credentials. 

On the HTPC I have tried:
Restarting smbd and nmbd
Creating a test share, which had the same result
Even rebooted the whole computer

On the Win7 laptop:
Rebooted (hadn't been done in a million years)
Connecting directly to share name (ie: \\mediabox\testing)
Tried connecting to a share name specifying user:nobody
Logging in with user set up on the htpc

Windows can see it fine, just wants login credentials. but I don't know if it's a Windows problem, or a Samba issue and mine just works because it's also Ubuntu.

---

