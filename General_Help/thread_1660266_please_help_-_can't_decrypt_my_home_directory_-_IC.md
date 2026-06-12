---
title: "please help - can't decrypt my home directory - ICE login error"
date: 2011-01-05
forum: General Help
---

### Post by ubu-for on 2011-01-05
I know some people here in the forum had already similar problems and got some promising hints but I'm trying to get my system working since 2 weeks and have no further clue.

I've changed my user-password and the result was an ICEauthority login error. After some commands I can login into my account again but now I have a brand new home directory and a second with my encrypted files.



/home/user (brand new)

/home/.ecryptfs/user/.ecryptfs
/home/.ecryptfs/user/.Private   (encrypted files)



Now I've no longer access to my encrypted home directory after the login even though I've changed my user-password to the old one (when everything worked fine).

I've already tried some commands but couldn't decrypt the files.



user@ubuntu:/$ sudo mount -t ecryptfs /home/.ecryptfs/user/.Private /home/.ecryptfs/user/Private -o ecryptfs_cipher=aes,ecryptfs_key_bytes=16,key=passphrase
Passphrase: 
Enable plaintext passthrough (y/n) [n]: y
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [aef7c05739623791]: aef7c05739623791
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=aef7c05739623791
  ecryptfs_passthrough
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=aef7c05739623791
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [aef7c05739623791] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Mounted eCryptfs



The result was I have now the same encrypted files also in "/home/.ecryptfs/user/Private" like in "/home/.ecryptfs/user/.Private" before.

Every hint would be appreciated!

---

### Post by ubu-for on 2011-01-05
Thanks to clivejo I can decrypt my data again!

[http://ubuntuforums.org/showpost.php?p=10208094&postcount=15](http://ubuntuforums.org/showpost.php?p=10208094&postcount=15)

---

