---
title: "w32 codecs permission denied?"
date: 2006-03-12
forum: General Help
---

### Post by matthinckley on 2006-03-12
I try to wget the w32 codecs just as it says to in the wiki.. with this command

```
wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
```

and I get this response..

```
--12:33:37--  ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
           => `w32codecs_20050412-0.0_i386.deb'
Resolving ftp.nerim.net... 62.4.17.14, 2001:7a8:1:5::14
Connecting to ftp.nerim.net|62.4.17.14|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /debian-marillat/pool/main/w/w32codecs ... done.
==> PASV ... done.    ==> RETR w32codecs_20050412-0.0_i386.deb ... done.
w32codecs_20050412-0.0_i386.deb: Permission denied

```

anyone know what I'm doing wrong?

Thanks

Matt

---

### Post by matthinckley on 2006-03-12
nevermind.. its working now

---

