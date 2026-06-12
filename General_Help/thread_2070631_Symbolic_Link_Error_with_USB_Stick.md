---
title: "Symbolic Link Error with USB Stick"
date: 2012-10-13
forum: General Help
---

### Post by Samurai Penguin on 2012-10-13
I used to be able to make a link on my USB stick and then move it to the Ubuntu 12.04 desktop. I formatted the stick in Windows XP, used FAT32 and re-installed all the files onto the stick. When I booted into Ubuntu I could not make any links on the stick. Went to Win XP, formatted back to what it was (FAT) and still get the same error when I try to make a link (for a .txt doc) on the USB stick :

Error while creating link to DOC.txt

The target doesn't support symbolic links

---

### Post by The Cog on 2012-10-13
You cannot create symbolic links on FAT filesystems, and I don't think you can on NTFS either. Only *nix filesystems support symbolic links - ext*, xfs, jfs, btrfs etc. But in general, windows can't read *nix filesystems, not because they're secret but because MS doesn't like interoperability.

---

### Post by cool110 on 2012-10-13
Starting with Windows Vista you can have symbolic links on NTFS.

---

### Post by The Cog on 2012-10-13
> **cool110 said:**
> Starting with Windows Vista you can have symbolic links on NTFS.

Ooh. I didn't know that. Thanks.

---

### Post by Samurai Penguin on 2012-10-14
ah, that's what it was, I recently switched from Wind 7 which is NTFS

thanks for taking the time to reply ... :guitar:

---

