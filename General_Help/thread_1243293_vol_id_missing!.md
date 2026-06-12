---
title: "vol_id missing!"
date: 2009-08-18
forum: General Help
---

### Post by Infin1ty on 2009-08-18
I have a problem with the grub loader, it uses the vol_id (/sbin/vol_id) and i have it missing.
i ran apt-file search vol_id and i do have the udev package which is kinda odd that i have the vol_id missing.
i ran some search in google and figured out i have blkid! (and i haven't upgraded to karmic yet), now the problem is that update-grub currently uses vol_id and i get some errors on loading because of that.

anything i could do?

Thanks.

---

### Post by dcstar on 2009-08-19
> **Infin1ty said:**
> I have a problem with the grub loader, it uses the vol_id (/sbin/vol_id) and i have it missing.
i ran apt-file search vol_id and i do have the udev package which is kinda odd that i have the vol_id missing.
i ran some search in google and figured out i have blkid! (and i haven't upgraded to karmic yet), now the problem is that update-grub currently uses vol_id and i get some errors on loading because of that.

anything i could do?

Thanks.
Try:
```
sudo ln /lib/udev/vol_id /sbin/vol_id
```

---

### Post by Infin1ty on 2009-08-19
> **dcstar said:**
> Try:
```
sudo ln /lib/udev/vol_id /sbin/vol_id
```

yeah, i tried that already, i figured out where the "binaries" sits, but i just dont have vol_id..
this is really weird..
any suggestions?

---

### Post by stpg on 2009-10-30
> udev (141-3+gitf079968) karmic; urgency=low

  * Update to GIT HEAD:
    - vol_id removed, rules converted to using blkid.

Use blkid, luke!

---

