---
title: "ftp vs sftp"
date: 2010-08-06
forum: General Help
---

### Post by Vtsedi on 2010-08-06
When would ftp be a better choice than sftp?

---

### Post by andrewc6l on 2010-08-06
FTP exists because it was around long before sftp.

FTP requires its own server; sftp uses the same server as ssh. If you don't want to allow ssh to a machine but do want to allow file transfer, you could set up ftp.

sftp encrypts, so it takes longer than ftp. If you have an internal network you trust, ftp could move data faster. (Although if you trust the network that much, might as well set up a shared file system. Sometimes you don't have the option.)

If you want an anonymous file transfer mechanism (ie not having to log in under a certain account) FTP will allow it, and I don't think sftp will.

You can chroot ftp; I don't know if you can chroot sftp.

For everything else, sftp is much better.

---

