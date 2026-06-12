---
title: "Ubuntu 11.10 instalation failed."
date: 2011-10-13
forum: General Help
---

### Post by jjscorn on 2011-10-13
This is the error:

Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/pool/universe/g/gmp4/libgmp3c2_4.3.2+dfsg-2ubuntu1_amd64.deb](http://pt.archive.ubuntu.com/ubuntu/pool/universe/g/gmp4/libgmp3c2_4.3.2+dfsg-2ubuntu1_amd64.deb) 403  Forbidden


Someone help?

---

### Post by effenberg0x0 on 2011-10-13
Repos are not synced. Either you will edit your /etc/apt/sources.list and replace **pt**.xxxxxxxxxxx for **us**.xxxxxxxxx or wait till they are synced.

Test:
**us**.archive.ubuntu.com/ubuntu/pool/universe/g/gmp4/libgmp3c2_4.3.2+dfsg-2ubuntu1_amd64.deb

Same file, US repo, work.

Regards,
Effenberg

---

