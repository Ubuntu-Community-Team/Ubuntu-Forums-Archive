---
title: "How to set up encrypted directory like the default Ubuntu encrypted home directory"
date: 2011-12-26
forum: General Help
---

### Post by jsmtrd on 2011-12-26
How would one go about setting up a encrypted directory that is like the default Ubuntu encrypted home directory, and mounted automatically at log in. I have my home directory encrypted and would like to keep incremental backups in another partition, but would like them to be encrypted as well. The other partition is not removable so should be mounted at log in time so the backup program can find it as needed. It should also contain all the date needed to be mounted and unencrypted, when the home directory is not available.

---

### Post by 2F4U on 2011-12-26
Here is an introduction on how to encrypt file systems:

[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

---

### Post by jsmtrd on 2011-12-26
> **2F4U said:**
> Here is an introduction on how to encrypt file systems:

[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)


Thanks for the link.  However I am not sure this is what I want. Is "dm-crypt/LUKS/cryptsetup" the same thing as "ecryptfs"? I believe the current version of ubuntu uses ecryptfs to encrypt the home directory. I thought I would use the same thing so as not to have two different encryption systems running on my system, and so that I could use the same way to manually mount the file system if my system totally brakes.

---

