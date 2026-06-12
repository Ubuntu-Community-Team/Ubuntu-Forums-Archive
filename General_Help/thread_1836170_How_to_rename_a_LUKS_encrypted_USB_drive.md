---
title: "How to rename a LUKS encrypted USB drive?"
date: 2011-08-30
forum: General Help
---

### Post by Jarretinha on 2011-08-30
Dear all,

I've got a external USB 2.0 HD ext4-formated with a lot of sensible information. I've encrypted it using LUKS. Everything went fine until I've noticed my complete ignorance on how to rename it after the process. udev seems to mount it using a fixed "fake" UUID:

```
/dev/mapper/cryptswap1: UUID="bada0f72-b22f-4e65-9b53-0ff58b3f5e65" TYPE="swap" 
/dev/sdb1: UUID="26f78762-25d9-47eb-9a3c-87f225de6386" TYPE="crypto_LUKS" 
/dev/mapper/udisks-luks-uuid-26f78762-25d9-47eb-9a3c-87f225de6386-uid1000: UUID="f5f55b5f-7e69-4231-b550-6bc0d55494d0" TYPE="ext4"
```

The last UUID is the one that shows up in /media. So, where/how can change that behaviour and set a decent named mount point?

---

