---
title: "encfs chewing up CPU cycles"
date: 2011-04-14
forum: General Help
---

### Post by uriel1998 on 2011-04-14
I successfully encrypted my home folder post installation, following the instructions [here]("https://wiki.ubuntu.com/EncryptedHomeFolder").  By and large, I'm happy with it, and it's not a huge resource hog.

Except when it is.  Specifically, when anything's making lots of read/write calls, such as clamAV scanning a home directory, or SpiderOak scanning for changes, or my rdiff-based backup, cups-pdf trying to create a PDF, or (don't hate me, I have to use Word for work) Word 2007 saving files.  

When this happens, encfs (ps aux command below) just gobbles up CPU cycles like crazy.  Sometimes it pops as high as 90% CPU (according to htop), many times hovering around 30%.  Ugh.

I know *why* the behavior occurs (encryption/decryption on the fly);  I'm wondering if there's a way to mitigate the effects somewhat.  It's enough of an irritation and performance hit that I'm considering migrating back out of an encrypted home directory, even though I'd rather not.

Any help appreciated!

Ubuntu 10.04, running OpenBox as WM.  
 ```
encfs -S --idle=1 -v /home/.enc/MYUSER /home/MYUSER -- -o nonempty,allow_root,nonempty
```

---

