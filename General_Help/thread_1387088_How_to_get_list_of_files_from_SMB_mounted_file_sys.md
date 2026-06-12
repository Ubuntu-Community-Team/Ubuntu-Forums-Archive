---
title: "How to get list of files from SMB mounted file system"
date: 2010-01-21
forum: General Help
---

### Post by jcobban on 2010-01-21
I have my Win7 laptop connected using SMB (the only mode of connection supported by the Home edition of Win7) to my Ubuntu desktop.  Nautilus permits me to browse the file system and perform operations as if it was a local file system, but I cannot seem to get some command line tools to work.

Specifically when I ask ls to display the contents of a directory I get:

$ ls "smb://jcobban-laptop/users/jcobban/Documents/Archives/Ontario/Middlesex/Lucan"
ls: cannot access smb://jcobban-laptop/users/jcobban/Documents/Archives/Ontario/Middlesex/Lucan: No such file or directory

As I understand it the issue is that the support for SMB does not present the remote file system as a file system, the way that NFS does for example.  Hence the URL-style access method prefix on the "filename".

---

