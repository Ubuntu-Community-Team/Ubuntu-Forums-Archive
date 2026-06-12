---
title: "oops with tar. screwd up a file"
date: 2009-10-08
forum: General Help
---

### Post by Alice1cmd on 2009-10-08
Hi,

I wanted to tar a php file but I mixed up tar arguments lol.

I did:
tar -cvf file.php file.tar

instead of the other way...

Now `file file.php` says that the php file is a data file.

Is there a way to recover it? I'm fkd

---

### Post by geirha on 2009-10-08
No. Sounds like you've overwritten it beyond repair. It's due to these kinds of accidents that one generally does regular backups, and in the case of source code, also use version control systems.

---

