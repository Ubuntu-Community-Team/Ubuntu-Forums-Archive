---
title: "Can't upload via FTP"
date: 2011-07-16
forum: General Help
---

### Post by thunderofnl on 2011-07-16
every time I try to upload something via FTP it tells me:
> ERROR:> Requested action not taken (e.g., file or directory not found, no access).How do I give access to my ftp? (I try to upload to Desktop)
I use vsftpd.

Thanks in advance :)

---

### Post by bhinderm on 2011-07-16
Most likely a permissions problem, can you share the relevant part of your vsftpd.conf?

---

### Post by thunderofnl on 2011-07-16
I think I found the problem. **write_enable **was commented out..

Edit: Yes that was it... I really need to see the .conf first ;P

---

