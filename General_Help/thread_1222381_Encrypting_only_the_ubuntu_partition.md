---
title: "Encrypting only the ubuntu partition"
date: 2009-07-24
forum: General Help
---

### Post by akrchstn on 2009-07-24
Pretty much what the title says. Is there a way I can do a full disk encryption on just my ubuntu partition with truecrypt or is it called a full disk encryption for a reason?

---

### Post by SecretCode on 2009-07-25
TrueCrypt can mount an encrypted volume into an existing filesystem, and volumes can be file-hosted or entire partitions or entire drives. So you can certainly encrypt just one partition.

But if you want to encrypt the drive that Ubuntu boots from, you're out of luck as far as I know. TrueCrypt's "system encryption" only supports Windows at this point. [TrueCrypt - Free Open-Source Disk Encryption - Documentation - System Encryption](http://www.truecrypt.org/docs/?s=system-encryption)

There are other ways to do boot-partition encryption in Ubuntu - see for example [[ubuntu] [SOLVED] TrueCrypt System Drive Encryption - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=1024886).

---

