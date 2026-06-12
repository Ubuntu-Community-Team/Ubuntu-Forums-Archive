---
title: "Backing up ftp server"
date: 2010-07-11
forum: General Help
---

### Post by Little Blue on 2010-07-11
Hi,

I have access to a few ftp servers which I've been trying to work out a way to automate a data backup for them, but ftp is the only access I really have to them. I thought I was onto a winner when I found curlftpfs a few weeks ago since it allowed me to mount them and dump their files into a gzipped tar file saved locally, but it seems to have issues if there's a lot of files to transfer. Before long tar starts complaining along the lines of
```
/bin/tar: SOME_FILE: Warning: Cannot stat: No such file or directory
```

Can't understand why unless curlftpfs is closing the connection during the archiving...

So I'm asking if there's any more robust ways of mounting an ftp server or even backing up one in general?

Any thoughts?

---

