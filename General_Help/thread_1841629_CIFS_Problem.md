---
title: "CIFS Problem"
date: 2011-09-09
forum: General Help
---

### Post by jrmolinaq on 2011-09-09
Hi, I mounted a CIFS folder and the mount is OK, in the console I can see all the files with all the permissions but when I try to open a document I have the error "permission denied".

The complete problem is when I mount a CIFS that is OK (I can read and open documents), this mounted folder is shared with "net usershare add name /path name everyone:F guest_ok=y". And this shared folder is mounted again with CIFS, this last mount is mounted fine, the files are mounted and have all the permissions but I can`t open them.

When the first mount is made with webdav the final mount allow to open documents, if the first is cifs the problem occurs.

Can anybody help me?

Thanks for your time

---

### Post by jrmolinaq on 2011-09-09
I use ubuntu 10.10 server edition 64 bits.

---

### Post by jrmolinaq on 2011-09-12
Can anybody help me?

---

