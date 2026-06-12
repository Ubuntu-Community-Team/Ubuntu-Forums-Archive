---
title: "issues using the NTFS Configuration Tool"
date: 2009-11-29
forum: General Help
---

### Post by Matt26 on 2009-11-29
i'm trying to use the latest version of the NTFS Configuration Tool in ubuntu 9.10 to mount a couple of internal NTFS drives, and i can't specify the directory that i have created under my home folder as the mount point- i get an error message indicating it is looking for a name, not a directory.

does anyone know what i might be doing wrong here?

also, does the NTFS Configuration Tool support mounting of network NTFS drives?

thanks.

---

### Post by grizzler on 2009-11-29
> **Matt26 said:**
> i'm trying to use the latest version of the NTFS Configuration Tool in ubuntu 9.10 to mount a couple of internal NTFS drives, and i can't specify the directory that i have created under my home folder as the mount point- i get an error message indicating it is looking for a name, not a directory.

does anyone know what i might be doing wrong here?
Nothing, other than expecting too much from that tool. I had the same issues with it. It stubbornly insists on plonking the mount point in /media, no matter what. So I let it and manually changed the fstab file (and removed the unused stuff from /media) afterwards.

> also, does the NTFS Configuration Tool support mounting of network NTFS drives?
No idea, sorry.

---

