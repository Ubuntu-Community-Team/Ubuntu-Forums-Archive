---
title: "having trouble booting XP.."
date: 2011-09-18
forum: General Help
---

### Post by owners4life5 on 2011-09-18
hello,

i have a desktop with two hard drives. recently, one master 80gb has had xp installed, and a 160gb slave for storage (music, mostly). but today i wanted to install 10.10 onto the master. so i went through the setup process and specified partitions manually. all i really did was resize the 80gb xp partition to 40gb, added a 2gb swap space, and made a 38gb ubuntu installation. i marked the ubuntu installation as a primary, and the swap as a secondary.

so now, when i boot, i'm offered the grub menu with 10.10, xp, memtest, etc.

when i select ubuntu it works fine, but when i select xp i'm provided with the following message:
```
Windows could not start because the follwing file is missing or corrupt:
<Windows root>\system32\hal.dll
please re-install a copy of the above file.
```

So i'm sort of at a standstill, and not exactly sure what to do.

any help is appreciated,
thanks.

---

### Post by TeoBigusGeekus on 2011-09-18
You should have defragmented the drive 5 or 6 times before proceeding with partitioning.
Grab a winxp cd, boot with it and try the repair option.
If it hopefully works, chances are that it could impair your grub, so check [this]("https://help.ubuntu.com/community/Grub2#ChRoot") out in case you need to reinstall it.

---

