---
title: "fsck: zero-length partition"
date: 2010-06-10
forum: General Help
---

### Post by sirpixalot on 2010-06-10
I am running Lucid Lynx 10.04 amd64. My system froze today and I was forced to shutdown manually by holding the power button.  Afterwards, I was unable to mount my /home directory -- during boot, I received messages complaining of errors.  I then booted into the a Live USB version of Lucid Lynx and ran the following command. Note: my /home is on /dev/sda3.  ```
 # fsck -y /dev/sda3  
fsck from util-linux-ng 2.17.2 e2fsck 1.41.11 (14-Mar-2010) fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3 Could this be a zero-length partition? 
```   Is there a way to recover from a "zero-length partition" complaint?  Any suggestions on how to recover my /home?

---

