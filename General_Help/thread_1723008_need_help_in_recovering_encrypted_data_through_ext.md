---
title: "need help in recovering encrypted data through external hard drive"
date: 2011-04-06
forum: General Help
---

### Post by kiddykoff on 2011-04-06
Hello forum,

I was trying to fix some hardware on my laptop and i ended up mucking the whole thing up. The HDD seems to fine though. I have it in a external HDD enclosure and it's plugged into my mothers desktop through usb.

I'm trying to print some files I have, but my home directory on the external HDD is encrypted.

I've tried the method [here]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually")
more specifically i used these commands
```
sudo ecryptfs-add-passphrase --fnek
sudo mount -t ecryptfs /media/d4dd9987-42c6-47ea-bccf-91b01a66bd27/home/kurtis/ /home/rose/Private

```

towards the end i get this,
```
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=7255ecfb83479420
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=3d1983c58fe67242
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : y
Would you like to proceed with the mount (yes/no)? : y
Would you like to proceed with the mount (yes/no)? : y
Would you like to proceed with the mount (yes/no)? : y
Would you like to proceed with the mount (yes/no)? : y
Aborting mount.
```

I really need to get these history notes off my computer and printed out. Help would be greatly appreciated.

---

### Post by kiddykoff on 2011-04-06
okay, i'm guessing the encrypted data is not in my /media/d4dd9987-42c6-47ea-bccf-91b07a66bd27/home/kurtis folder since it only has 2 files, so i must be going about this wrong.

---

### Post by kiddykoff on 2011-04-06
i just tried using the live cd method on the same web page and i'm getting the same problems

---

### Post by kiddykoff on 2011-04-06
i replaced a junk laptop's hdd with my hdd and it booted fine. it's a less than ideal solution, but i got my history notes. Now i need to study.

---

