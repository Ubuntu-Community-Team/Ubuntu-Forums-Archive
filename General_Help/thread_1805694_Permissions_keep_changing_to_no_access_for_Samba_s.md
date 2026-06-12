---
title: "Permissions keep changing to no access for Samba share directories."
date: 2011-07-16
forum: General Help
---

### Post by KillrBuckeye on 2011-07-16
I have a recurring problem with permissions for my directories shared via Samba.  The shared directory permissions keep resetting to  'd---------' (no access), and I have to manually open up access via 'chmod'.  I haven't been able to pinpoint the exact conditions that lead to the permissions reset, but it seems to happen after I've tried unsuccessfully to access the share from my WDTV media streaming device.  

The share is a hard drive volume mounted to a directory.  In this case it is mounted to '/share2_VidsMusic'.  It is configured in fstab as follows:

```
UUID=16f2ae3c-01ad-426b-b7b0-2c59d51d8502 /share2_VidsMusic  ext3 user 0 0
```

The share is setup in Samba as follows:
```
[share2_VidsMusic]
comment = Share 2: Video & Music
path = /share2_VidsMusic
browsable = yes
public = yes
writeable = yes
guest ok = yes
read only = no
create mask = 0777
force user = chris
```

Any help you can provide would be appreciated.

---

### Post by KillrBuckeye on 2011-07-17
Bump.

---

