---
title: "Shared Storage"
date: 2011-06-15
forum: General Help
---

### Post by abhishek456 on 2011-06-15
hi all,

i had installed Ubuntu on server. On top of it i installed KVM hypervisor and then again installed two UBUNTU virtual machines on top of KVM. I need a shared storage which can serve both virtual machines. Virtual machines will do both read and write operations.

Am running oracle on top of both virtual machine. data written by one oracle application from virtual machine on shared storage need to be accessed by oracle application on other virtual machine and vice-verse 

earlier i tried sharing a hard disk to two virtual machines with this fstab entry

```
/dev/sdb1   /mnt/share   ext3   rw,suid,dev,exec,auto,users,sync   1  1
```

i assumed that sync option will immediately push data to hard disk with out storing data in cache, so that changes will be visible on other linux machine immediately.
But i cannot achieve required things by doing as above

Changes are visible if i un-mount and re-mount hard disk again

Can anyone suggest me how to make setup for shared storage.

Do i need to setup NFS for this or can i make it with normal hard disk

---

### Post by abhishek456 on 2011-06-17
any suggestionssssssssss

????????????????????????????

---

