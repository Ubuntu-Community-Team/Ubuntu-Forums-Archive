---
title: "smbfs vs cifs Difference"
date: 2009-06-26
forum: General Help
---

### Post by measekite on 2009-06-26
I know that smbfs and cifs are interchangeable in an fstab file but what is the difference and which should you use?

Case 1
Linux Client wants to read and write to a Windows Server

Case 2
Linux Client wants to read write to a Linux Server

Case 3
Linux Client wants to read write to and from another Linux Client

And when should you use nfs?

For what ever it is worth I spend a lot of time (a day) trying to get my fstab to mount properly using Samba on Jaunty.  I had no such problem when using Feisty.  I even went to Synaptic and reinstalled Samba.

Finally I came across a thread where the person claimed that for some quirk he had the same problem on one of his two machines.  He told me to do this:

```
apt-get install smbfs
```

Apparently that was not installed.  **It Worked.**

Still get the CIFS VFS Server Not Responding on shutdown hanging the system for 1 to 2 minutes.  This has been going on for some time and over a few years nobody fixed it.  That is shameful.

---

