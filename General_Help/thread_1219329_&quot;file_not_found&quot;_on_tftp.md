---
title: "&quot;file not found&quot; on tftp"
date: 2009-07-21
forum: General Help
---

### Post by lumix on 2009-07-21
One day something will "just work", I just know it.


Mean time, I've set up tftp-hpa with:

```

#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /tftpboot"

```

in /etc/default/tftpd-hpa.

I get "file not found" when trying to "get" a file that is indeed there.  Tried changing permissions and owners, but how to know who should own it?  Maybe that's not the issue, anyhow.  No idea where to begin looking from here, but I've already tried google.

---

### Post by bacil on 2009-07-21
have you got rights to the file or folder where the file is ?

---

### Post by lumix on 2009-07-21
Well, who should own the files so that any random user (i.e. diskless, pxe boot workstations) can get them?

---

### Post by lumix on 2009-07-21
The problem wasn't permissions at the source (/tftpboot), it was at the destination.  I happened to be in / and didn't notice, so I was denied the write, not the read.

Thanks for the reply.

---

