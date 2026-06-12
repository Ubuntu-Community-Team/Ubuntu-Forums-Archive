---
title: "Can't recover mount passphrase"
date: 2012-01-14
forum: General Help
---

### Post by xtheunknown0 on 2012-01-14
Hello,

One of my laptops suddenly died. I've taken out the hard disk and attached it via USB-SATA cable to another laptop and am using 10.04 Live CD right now. The Linux partition has automatically been mounted. To decrypt the home folder, I've tried
```
ecryptfs-unwrap-passphrase /media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home/user/.ecryptfs/wrapped-passphrase
``` from [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase) and entered the login password for user but I get
```
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs
```
Am I doing something wrong?

TIA,
xtheunknown0

---

### Post by Cheesemill on 2012-01-14
Have you done what it says and checked the system log?

---

### Post by xtheunknown0 on 2012-01-14
> **Cheesemill said:**
> Have you done what it says and checked the system log?

No. Could you please tell me how to?

TIA,
xtheunknown0

---

### Post by xtheunknown0 on 2012-01-15
Bump

---

