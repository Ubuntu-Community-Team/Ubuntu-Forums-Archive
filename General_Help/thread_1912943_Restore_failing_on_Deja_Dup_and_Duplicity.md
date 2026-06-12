---
title: "Restore failing on Deja Dup and Duplicity"
date: 2012-01-21
forum: General Help
---

### Post by machsimus on 2012-01-21
Hey everyone, I had an automatic backup running through deja dup on an older gateway with Ubuntu 11.10 running on it. I had just copied all of my pictures from my laptop to this desktop. My wife copied our Christmas pictures to it and it backed up, encrypted.

Fast forward, that computers hd took a dump and I am trying to restore those pictures to another Ubuntu desktop. Deja Dup is not recognizing the password and when I run duplicity from the terminal, I get the following:

Synchronizing remote metadata to local cache...
> GnuPG passphrase: 
Copying duplicity-new-signatures.20111231T132755Z.to.20120109T025312Z.sigtar.gpg to local cache.
GPGError: GPG Failed, see log below:
===== Begin GnuPG log =====
gpg: CAST5 encrypted data
gpg: encrypted with 1 passphrase
gpg: fatal: zlib inflate problem: invalid literal/length code
secmem usage: 2272/2432 bytes in 6/7 blocks of pool 2432/32768
===== End GnuPG log =====In that directory, there is a full backup and an incremental. Its about 55GB worth of pictures.

Any ideas?

Thanks in advance.

---

### Post by machsimus on 2012-01-22
Well, I removed the full backup files into their own folder outside of the incremental files and the restore started through Deja Dup. Its running now and I am crossing my fingers. If this works, I'll try the incremental files next.

---

