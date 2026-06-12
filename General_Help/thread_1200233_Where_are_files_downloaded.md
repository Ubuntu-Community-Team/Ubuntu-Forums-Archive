---
title: "Where are files downloaded?"
date: 2009-06-29
forum: General Help
---

### Post by LarryMi on 2009-06-29
I downloaded a deb package from getdeb.net.  During the install process, it wanted to download 73 files, and because is took so long for the 5th file, I decided to cancel the process.

Can someone please tell me where the 4 files it downloaded are stored so I can delete them?

Thanks.

---

### Post by rraj.be on 2009-06-29
If you are installing using synaptic

it will be here

> /var/cache/apt/archives

Mostly incomplete downloads can resume on next attempt of installation.

---

### Post by colau on 2009-06-29
> **LarryMi said:**
> I downloaded a deb package from getdeb.net.  During the install process, it wanted to download 73 files, and because is took so long for the 5th file, I decided to cancel the process.

Can someone please tell me where the 4 files it downloaded are stored so I can delete them?

Thanks.
If you need you can delete them from there too.
```

cd /var/cache/apt/archives
sudo aptitude clean

```

---

