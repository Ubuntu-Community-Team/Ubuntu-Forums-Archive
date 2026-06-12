---
title: "trouble with curlftpfs"
date: 2009-08-16
forum: General Help
---

### Post by Error403 on 2009-08-16
Hello,

I am trying to use curlftpfs to mount a ftp server as a directory, but everytime I do that and I try to access it it works very slowls and gives i/o errors. Changing directory to it gets very slow, and ls gives the i/o error.  I'm still on 8.04 LTS in cli mode only. 

I use:

```
curlftpfs -o user=user:pass ftp://example.no-ip.com
```

Any ideas what I might be missing?

---

