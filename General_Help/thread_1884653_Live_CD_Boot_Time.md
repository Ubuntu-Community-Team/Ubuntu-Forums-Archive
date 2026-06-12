---
title: "Live CD Boot Time?"
date: 2011-11-21
forum: General Help
---

### Post by halw on 2011-11-21
How long does it take for Ubuntu 11.10 live cd to get to a usable desktop?

I get to the point where I select 'Try Ubuntu' and have not gotten a desktop yet. Maybe 10 to 15 minutes have elapsed.

This is occurring on an AMD Athlon 64 with 2GB ram and, fwiw, a 250Gb hard drive.

---

### Post by Gremlinzzz on 2011-11-21
10 to 15 minutes is too long
 3 minutes tops

---

### Post by halw on 2011-11-21
CD was burned at 4x. Not sure what the issue may be.

Is there any sort of log that can be looked at by going to CL if possible?

---

### Post by ajgreeny on 2011-11-21
Did you check the .iso file's md5sum which you can find at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")?   If you did not do that your problem may be a corrupt file, and therefore a corrupt CD.

---

### Post by halw on 2011-11-21
> **ajgreeny said:**
> Did you check the .iso file's md5sum which you can find at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")?   If you did not do that your problem may be a corrupt file, and therefore a corrupt CD.

```
 md5sum ubuntu-11.10-desktop-i386.iso
c396dd0f97bd122691bdb92d7e68fde5  ubuntu-11.10-desktop-i386.iso
```

Md5sum hash checks OK.

Edit: Downloaded 11.10 from BitTorrent, burned another cd and, wouldn't you know it, this time it booted. Not sure where I picked up the advice but, thanks.

---

