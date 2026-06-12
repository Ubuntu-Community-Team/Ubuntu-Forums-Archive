---
title: "lftp truncates files' datetime"
date: 2009-07-26
forum: General Help
---

### Post by saybye on 2009-07-26
Hello.
I'm trying to use lftp for backuping local data to the ftp server. (Since this is my webhosting provider's server, I have no other choice but to use ftp. No rsync. no ssh)

The problem is, that lftp truncates datetime of the files to minutes, i.e. local date 28.4.2009 06:20:37 is truncated to 28.4.2009 06:20:00 on the server. Therefore all remote files are deleted and replaced by local files everytime I start mirroring - even with the --only-newer option. 
In other words: No metter what I am doing, local files are always "newer" and so lftp always transfers all data from local host to the server.

Can anybody help me with this issue? I don't believe this is how lftp is meant to work.

Thanks,
Jakub

---

