---
title: "rc.local mounts too late."
date: 2010-06-23
forum: General Help
---

### Post by phr0ze on 2010-06-23
I run this in rc.local

sleep 10
/bin/mount -a -t cifs
sleep 5
/bin/mount /var/ftp/gldlff/filesd


It solves my mount problems for the most part. However when mediatomb starts, it starts at 98, this starts at 99 so mediatomb doesn't see the mounts it needs.

What is the proper way this should have been done? I assume I could always create the same bit in a script and run it at 97 instead, but I still feel it's hackish.

Thanks.

---

### Post by phr0ze on 2010-06-24
Bueller...

---

