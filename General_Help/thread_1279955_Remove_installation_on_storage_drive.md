---
title: "Remove installation on storage drive"
date: 2009-10-01
forum: General Help
---

### Post by PurposeOfReason on 2009-10-01
Just a quick question I need confirmation on. My server has debian installed on a 750GB drive that has a storage partition on it. I'm going to do a reinstall with gentoo on it's own drive. Would it be safe to then mount the 750gb drive and just delete / or would that take the mountpoint /750 with it? I'm assuming it would.

---

### Post by cariboo on 2009-10-01
If your main distribution is going to be Gentoo on it's own hard drive, you don't need to do anything with the 750Gb drive. You won't be booting from it, so / won't be mounted.

---

### Post by PurposeOfReason on 2009-10-01
I understand that, but there are about 5GB I could salvage from it, I guess I could just delete most things and call it good.

---

