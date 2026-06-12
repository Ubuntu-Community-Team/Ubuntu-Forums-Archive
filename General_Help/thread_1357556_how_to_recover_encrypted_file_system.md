---
title: "how to recover encrypted file system"
date: 2009-12-17
forum: General Help
---

### Post by mahmater on 2009-12-17
I had installed ubuntu 9.10 with the option of encrypting the disk (a foolish move which I needn't and shouldn't have done), now for some unknown reason my user acoount was broken and I couldn't recover my data as usual via Live CD,or other accounts (a friend suggested to create an another admin account).All it gave me is this:

---

### Post by itang sanjana on 2009-12-17
Perhaps this article could help you. Fingers crossed here .. [-o<
[http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

HTH,

---

### Post by SPr on 2009-12-17
[[SOLVED] fresh install with encrypted home partition](http://ubuntuforums.org/showthread.php?t=1305339)
It worked for one so it may work for you.
> 
edit: Solved. Noticed there was also a symlink in the home directory from .Private to /var/lib/ecryptfs so I put my backup copy of that back in place, logged out and back in and it mounted!


---

### Post by Dodominyk on 2009-12-21
[COLOR="Red"]**Update: Ok, this doesn't work after having rebooted. Maybe the reason why this was working is because during the same session I tried a bunch of other ecryptfs commands. See my next post below.**[/COLOR]

That webpage was a life saver, I hadn't seen anywhere the step:
```
$ sudo ecryptfs-add-passphrase --fnek
```
What's on that page is just a little bit different from what I finally had to do. If that's interesting to anyone, here is what I did:

First, it turns out that the passphrase that we were supposed to write down can be retrived as follows in case you lost it:
```
$ ecryptfs-unwrap-passphrase /mnt/old/home/.ecryptfs/user/.ecryptfs/wrapped-passphrase
Passphrase:   **<---- Here I entered my old ubuntu password**
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

```

Then
```
$ sudo ecryptfs-add-passphrase --fnek
Passphrase:   **<---- Here I entered XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX**
Inserted auth tok with sig [YYYYYYYYYYYYYYYY] into the user session keyring
Inserted auth tok with sig [ZZZZZZZZZZZZZZZZ] into the user session keyring
```

Then
```
$ mkdir /home/user/old-home
$ sudo mount -t ecryptfs /mnt/old/home/.ecryptfs/user/.Private /home/user/old-home
Passphrase:   **<---- Here I entered my old ubuntu password again**
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
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: **<---- Here y**
Filename Encryption Key (FNEK) Signature [MMMMMMMMMMMMMMMM]: **<---- Here ZZZZZZZZZZZZZZZZ**
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=ZZZZZZZZZZZZZZZZ
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=MMMMMMMMMMMMMMMM
Mounted eCryptfs

```

Here you go, it's mounted in /home/user/old-home.

It also turns out that if I unmount it and want to remount it, I need to do the 'sudo ecryptfs-add-passphrase --fnek' step before, everytime. Is this the same for everyone? Is there a way to avoid it? In particular, is there a way to automate all this?

---

### Post by Dodominyk on 2009-12-21
So now I proceed in 3 steps:

```
$ ecryptfs-unwrap-passphrase /mnt/old/home/.ecryptfs/user/.ecryptfs/wrapped-passphrase
Passphrase: **<---- old ubuntu pass**
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

```

```
$ printf "%s" "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" | sudo ecryptfs-add-passphrase --fnek -
Inserted auth tok with sig [YYYYYYYYYYYYYYYY] into the user session keyring
Inserted auth tok with sig [ZZZZZZZZZZZZZZZZ] into the user session keyring
```

```
$ sudo mount -t ecryptfs /mnt/old/home/.ecryptfs/user/.Private /home/user/old-home -o rw,ecryptfs_sig=YYYYYYYYYYYYYYYY,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_fnek_sig=ZZZZZZZZZZZZZZZZ,passphrase_passwd=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX,ecryptfs_passthrough=n
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=ZZZZZZZZZZZZZZZZ
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=YYYYYYYYYYYYYYYY
Mounted eCryptfs
```

Still, I need to do the 'sudo ecryptfs-add-passphrase --fnek' step before, everytime. Again, is this the same for everyone? Is there a way to avoid it? In particular, is there a way to automate all this without explicitely writing any password down, only the old ubuntu password would be input?

---

### Post by Nphyx on 2009-12-21
You're a lifesaver, man! I just had a major hard drive failure last week, and was able to recover part of the data but could not figure out how to decrypt my old home. If I had attempted this 15 hours earlier (before you posted) I'd have been at a total loss, great timing!

---

