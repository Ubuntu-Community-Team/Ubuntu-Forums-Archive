---
title: "USB drive not accessable"
date: 2009-08-24
forum: General Help
---

### Post by echo314 on 2009-08-24
I can see it in Computer as "USB drive", but cannot access it anymore. 

```
[  839.446446] end_request: I/O error, dev sdb, sector 0
[  839.446450] Buffer I/O error on device sdb, logical block 0

```

```
echo@echo-desktop:~$ dmesg | tail
[  942.313599] sd 6:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  942.313603] sd 6:0:0:0: [sdb] Add. Sense: Recorded entity not found
[  942.313608] end_request: I/O error, dev sdb, sector 0
[  942.456102] end_request: I/O error, dev sdb, sector 0
[  942.456841] end_request: I/O error, dev sdb, sector 0
[  944.778597] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  944.778603] sd 6:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  944.778608] sd 6:0:0:0: [sdb] Add. Sense: Recorded entity not found
[  944.778612] end_request: I/O error, dev sdb, sector 0
[  944.779464] end_request: I/O error, dev sdb, sector 0

```

---

### Post by echo314 on 2009-08-25
This drive does have a particularly important keyfile of mine...

---

### Post by echo314 on 2009-08-25
Its the keyfile to my password database. with my financial passwords. convenient for paying my credit card balance online...

---

