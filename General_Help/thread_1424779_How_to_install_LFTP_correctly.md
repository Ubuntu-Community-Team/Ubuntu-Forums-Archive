---
title: "How to install LFTP correctly"
date: 2010-03-08
forum: General Help
---

### Post by mokachoka on 2010-03-08
Can anyone run me through the process to install lftp correctly with all the correct support for SSL and SSH connections?
 
I am using the newest version of Ubuntu.

---

### Post by mokachoka on 2010-03-08
I have downloaded lftp-4.0.5.tar.gz from the LFTP site.
 
issued  sudo tar -zxvf lftp-4.0.5.tar.gz

cd into lftp-4.0.5
 
sh ./configure
 
it has come back with 
 
configure: WARNING: No terminfo
checking for readline... configure: error: need installed readline-devel package
 
Can anyone tell me what needs to be done now? This is my first time attempting to compile something.

---

### Post by gmargo on 2010-03-08
Why don't you just install the **lftp** package from the repository?

---

### Post by mokachoka on 2010-03-08
I have been using that version for the past few months but i keep getting buffer overflows on a few SFTP accounts and im not able to connect to FTPS servers. I thought by compiling a newer version maybe the buffer overflow issue at least would be resolved.

---

### Post by dontbugmee on 2010-05-23
You'll need to install the **libreadline-dev** package, as well as any other dependencies.```
sudo apt-get install libreadline-dev
```

---

