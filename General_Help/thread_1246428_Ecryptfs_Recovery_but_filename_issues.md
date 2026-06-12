---
title: "Ecryptfs Recovery but filename issues"
date: 2009-08-21
forum: General Help
---

### Post by Coops on 2009-08-21
I'm trying to restore an encrypted home directory from an external drive (taken from a broken machine). I've done it before, but this time I can't get it to un-encrypt the filenames!

Any help on where I'm going wrong would be much appreciated...

###### Recover Passphrase
```

root@t42:/mnt/se/home/hcooper# ecryptfs-unwrap-passphrase /mnt/se/var/lib/ecryptfs/hcooper/wrapped-passphrase <password>
Warning: Using default salt value (undefined in ~/.ecryptfsrc)
0eeeabd98b712xxxxxxxc99615aeed3

```


###### Mount ~/.Private
```

root@t42:/mnt/se/home/hcooper# mount -t ecryptfs .Private priv-mount/
Passphrase: <Copy and paste>
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
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
Enable filename encryption (y/n) [n]: y
Filname Encryption Key (FNEK) Signature [355a8158f7263d73]: 
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=355a8158f7263d73
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=355a8158f7263d73
Mounted eCryptfs

```

###### But files still encrypted!
```

root@t42:/mnt/se/home/hcooper# ls priv-mount/ | head
ECRYPTFS_FNEK_ENCRYPTED.FWbV5bgYtAXkGUQkHQDy-741RhF0Oj9RLat01azIzg2-Bmv09aTP.798yk--
ECRYPTFS_FNEK_ENCRYPTED.FWbV5bgYtAXkGUQkHQDy-741RhF0Oj9RLat02bjNe2K9A9yAtDtqVR2fKE--
ECRYPTFS_FNEK_ENCRYPTED.FWbV5bgYtAXkGUQkHQDy-741RhF0Oj9RLat03lQpO4z6uUwD9WsQiJJmN---
ECRYPTFS_FNEK_ENCRYPTED.FWbV5bgYtAXkGUQkHQDy-741RhF0Oj9RLat03Tdy2UfXOFXqg59QPgiufk--
ECRYPTFS_FNEK_ENCRYPTED.FWbV5bgYtAXkGUQkHQDy-741RhF0Oj9RLat03YCBiTiBPhUITveL61Ig5---
ECRYPTFS_FNEK_ENCRYPTED.FWbV5bgYtAXkGUQkHQDy-741RhF0Oj9RLat04U4m3v8nyfkYBzR0gIlurU--
ECRYPTFS_FNEK_ENCRYPTED.FWbV5bgYtAXkGUQkHQDy-741RhF0Oj9RLat05hOO7o-TwsvxYPcbsuFduk--
ECRYPTFS_FNEK_ENCRYPTED.FWbV5bgYtAXkGUQkHQDy-741RhF0Oj9RLat05IyxqDYKNvnaGQCucqCwR---
ECRYPTFS_FNEK_ENCRYPTED.FWbV5bgYtAXkGUQkHQDy-741RhF0Oj9RLat08Sn-h2I7Ve.H9QIQtJe3EE--
ECRYPTFS_FNEK_ENCRYPTED.FWbV5bgYtAXkGUQkHQDy-741RhF0Oj9RLat0aMjHBO9ledaiSZ6VMVYfJE--

```

---

### Post by tavitar on 2009-10-13
Having the exact same problem here.

I kept a record of the unwrapped passphrase as per instructions and I can mount the .Private as above but the filenames aren't unencrypted. I've checked the contents of the files and they look fine, it's only the filenames that are a problem.

The encrypted home was created in jaunty using 'sudo adduser --encrypt-home' and I'm attempting to mount it in karmic.

Any ideas?? Thanks,
Tav

---

### Post by pivert on 2009-10-21
Exactly the same problem here.

Created the encrypted home in Kubuntu 9.04, then I broke my kubuntu 9.04 because the update to 9.10 beta failed, and now I'm trying to access my home folder from the kubuntu 9.04 boot CD :

Here is a full example :
```

mount /dev/sda6 /mnt
ecryptfs-unwrap-passphrase /mnt/var/lib/ecryptfs/francoisd/wrapped-passphrase ( to get the passphrase )
mount -t ecryptfs /mnt/home/francoisd/.Private /mnt/mnt/disk 
root@ubuntu:/mnt# ecryptfs-unwrap-passphrase /mnt/var/lib/ecryptfs/francoisd/wrapped-passphrase
Passphrase:
Warning: Using default salt value (undefined in ~/.ecryptfsrc)
1adc57xxxxxxxxxxxxxxxxxxxxxxxxxx
root@ubuntu:/mnt# mount -t ecryptfs /mnt/home/francoisd/.Private/ /mnt/mnt/disk
Passphrase:
Select cipher:
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
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
Enable filename encryption (y/n) [n]:
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=5799f79f28afb688
Mounted eCryptfs
root@ubuntu:/mnt#
root@ubuntu:/mnt# cat /mnt/mnt/disk/ECRYPTFS_FNEK_ENCRYPTED.FWYOqZ3K1XygZUQeuE-oWWKAma0H3H8WGTg8SgxDEWyeChS-.YwzWFxDJ---
# Machine-generated file - use setup menu in minicom to change parameters.
pu port             /dev/ttyUSB0
pu baudrate         9600
pu rtscts           No
root@ubuntu:/mnt#

```

The content of the files is decrypted.
How can I get the filenames unencrypted ?

Regards

---

### Post by Antti Kaijanmäki on 2009-10-26
I had the same problem this weekend trying to access backup of an ecrypted home directory. I wrote a blog post about it:

[http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

Hopefully that's useful.

---

### Post by tavitar on 2009-10-26
Brilliant Antti, I now have unencrypted filenames.

The missing peice of the puzzle was:
> sudo ecryptfs-add-passphrase --fnek

Many thanks for the blog,
Tav

---

