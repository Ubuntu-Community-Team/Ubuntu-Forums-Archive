---
title: "Simple Backup Configure"
date: 2011-03-04
forum: General Help
---

### Post by rdharper on 2011-03-04
I have been using Simple Backup and backing up to a NAS drive on my local network.
The NAS drive can be accessed as a Windows Share entering the local address 192.168 etc.
A recent Ubuntu Update has wiped the Simple Backup configuration settings.
It no longer accepts the local address giving "The selected destination is not writable with current permissions" as if it needs a password - It doesn't have one.

However, the Backup Restore will restore from my last backup on the NAS drive.

Any suggestions to how I can get it to access the NAS drive?

---

### Post by rewyllys on 2011-03-04
I realize that this doesn't answer your question directly, but, FWIW, I've had very good results using LuckyBackup.

---

### Post by seawolf167 on 2011-03-04
Can you simply change ownership of the networked drive (i.e. its probably owned by root)?

```
sudo chown username:username /mounted/backup/location
```

---

