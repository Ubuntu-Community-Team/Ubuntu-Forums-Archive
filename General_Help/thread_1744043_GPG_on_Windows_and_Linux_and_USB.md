---
title: "GPG on Windows and Linux and USB"
date: 2011-04-30
forum: General Help
---

### Post by bcn17 on 2011-04-30
Recently I set up my GPG so that it runs from a folder on my USB drive. I like to think that this is more secure. Anyway, I have also done something horrible... I am trying to get it set up with windows. GPG4Win installs GPA just fine, And, I have found the gpg.conf file under C:/Users/bryan/AppData/Roaming/gnupg/gpg.conf. 

Here is my dilemma. I want to create a conf file very similar to my normal linux gpg.conf (but  pointing to the usb drive using whatever terminology is necessary like "D:/keyring" ). However, I have my keyring on an ext3 partition because it needs to be that way to handle permissions in ubuntu. Of course, windows can't read ext3, except through a special window like "ext2explore.exe". 

I would love to have a USB drive that allows me to jump around from OS to OS with my GPG keys. 

Here is my gpg.conf:

```
no-greeting

verbose
verbose

	no-default-keyring
	keyring		/media/ext3/keyring/pubring.gpg
	primary-keyring	/media/ext3/keyring/pubring.gpg
#	secret-keyring	/media/SD2/gnupg/v-master.gpg
	secret-keyring	/media/ext3/keyring/secring.gpg
	trustdb-name	/media/ext3/keyring/trustdb.gpg

personal-cipher-preferences AES256 TWOFISH CAMELLIA256 AES192 CAMELLIA192 AES CAMELLIA128 BLOWFISH CAST5 3DES
personal-digest-preferences SHA512 SHA384 SHA256 SHA224 SHA1 RIPEMD160 MD5
personal-compress-preferences ZLIB BZIP2 ZIP Uncompressed

default-preference-list AES256 TWOFISH CAMELLIA256 AES192 CAMELLIA192 AES CAMELLIA128 BLOWFISH CAST5 3DES SHA512 SHA384 SHA256 SHA224 SHA1 RIPEMD160 MD5 ZLIB BZIP2 ZIP Uncompressed

#hidden-encrypt-to 
```

---

