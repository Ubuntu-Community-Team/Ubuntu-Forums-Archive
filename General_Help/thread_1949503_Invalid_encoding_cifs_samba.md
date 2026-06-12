---
title: "Invalid encoding cifs samba"
date: 2012-03-30
forum: General Help
---

### Post by jamborta on 2012-03-30
Hi,

I am trying to mount a samba share drive (samba 2.2) using cifs.
(the samba server is built-in my router - cannot really upgrade). There is a problem with certain folders/files, ubuntu does not display them correctly (characters like áé etc), but it works when I mount the drive directly.

I tried adding iocharset=utf8, and other variations, some places I saw adding codepage=cp1250 or codepage=unicode, but that seems deprecated in the latest cifs.

many thanks for your help.

---

