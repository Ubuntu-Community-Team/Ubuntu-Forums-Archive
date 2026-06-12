---
title: "NetCDP connection to Samba"
date: 2010-01-20
forum: General Help
---

### Post by feetwet on 2010-01-20
I just setup my samba server on ubuntu 9.10 server. I can successfully map a network drive from household PC's to the samba shares. I CANNOT however get NetCDP to successfully connect to the samba server as a NAS.   Any tips on this?

Trying to use NetCDP on multiple windows PC's to back them up to the NAS (samba)

---

### Post by feetwet on 2010-01-20
Do I need something like FreeNAS "on top of" samba?

---

### Post by wild168 on 2010-01-22
I don't think you need FreeNAS.

Just make sure the share is writable and the user you use for NetCDP has the write privilege. Also, check your samba configuration, make sure the new directories created are with write permissions.

---

### Post by feetwet on 2010-01-22
> **wild168 said:**
> I don't think you need FreeNAS.

Just make sure the share is writable and the user you use for NetCDP has the write privilege. Also, check your samba configuration, make sure the new directories created are with write permissions.

Correct it will work directly to Samba.

I got it to work last night. Each pc that uses NetCDP must use a different share location on the NAS, and yes permissions must be proper.

Still doing some validation of the backups.

---

### Post by wild168 on 2010-01-23
Actually, each PC doesn't have to have its own share. You can back up multiple PCs to the same share, which is what I do. I back up 3 PCs to the same share.

---

