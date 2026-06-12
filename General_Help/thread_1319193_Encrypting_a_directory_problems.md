---
title: "Encrypting a directory problems"
date: 2009-11-08
forum: General Help
---

### Post by Green_Star on 2009-11-08
I can create a private encrypted folder in my home folder. 
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

But I do not have much space in my OS drive. I would like to create a encrypted folder in another drive. How can I do that? All online available guides are showing creating a private folder in home directory.

By the way with above link, the password to decrypt the folder is my user account password, as this user name is shared with family, I would like to have another password, I couldn't find a solution to change that password. Any one knows?

---

### Post by Green_Star on 2009-11-15
Bump....

---

### Post by Green_Star on 2009-11-15
I have created a directory in other drive, and created a link to this directory in my private directory. I copied few files in to Private/link directory. After unmounting the private directory I can not see/read the files in Private directory, however I can access these files in other drive directory(these files copied into this directory thru the private directory), so my this experiment is failed. Can some one help me creating another encrypted directory? 

Another tried like below, it also failed.
> Sadira@Sadira:/mnt/disk01$ mkdir test-dir
Sadira@Sadira:/mnt/disk01$ chmod 700 test-dir/
Sadira@Sadira:/mnt/disk01$ mount -t ecryptfs /mnt/disk01/test-dir/ /mnt/disk01/test-dir/
mount: only root can do that
Sadira@Sadira:/mnt/disk01$ sudo mount -t ecryptfs /mnt/disk01/test-dir/ /mnt/disk01/test-dir/
[sudo] password for Sadira: 
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: y
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [10255d89eb2e0448]: 
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=10255d89eb2e0448
  ecryptfs_passthrough
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=10255d89eb2e0448
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
Sadira@Sadira:/mnt/disk01$

---

