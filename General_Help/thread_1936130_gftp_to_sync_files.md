---
title: "gftp to sync files?"
date: 2012-03-05
forum: General Help
---

### Post by Pacopag on 2012-03-05
Hi.  I use gFTP for file tranfers, and I've always done "Overwrite" by default.  Can gFTP be used to "sync" files, so it'll only transfer files that have been modified?

Also, what does the "Resume" action mean?

Thanks.

---

### Post by lechien73 on 2012-03-05
I don't know about gftp, but I know you can do this with lftp, since you can create script files for it. There's not a lot of documentation lying around for gftp, but everything I've read indicates that you can't.

The **Resume** action is for if the transfer is interrupted, the "resumed" data will be appended to the existing file instead of overwriting it.

---

