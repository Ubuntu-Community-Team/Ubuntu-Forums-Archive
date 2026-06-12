---
title: "Missing Headers?"
date: 2010-09-29
forum: General Help
---

### Post by GrantStoner on 2010-09-29
How do I know if my headers are properly installed? So far I've done```
grant@TheHaxLab:~$ uname -r
2.6.32-24-generic

grant@TheHaxLab:~$ uname -a
Linux TheHaxLab 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
```
But when I try to install certain things or remove certain things, I'll get a message during the installation or removal that says```
[Desktop Entry]-Header missing
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for python-support ...

```
Why?

---

### Post by Rubi1200 on 2010-09-30
Search in Synaptic for linux-headers; there should always be 2 files associated with each linux-image.

---

