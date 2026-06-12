---
title: "Upgrading Windows partition w/o losing Ubuntu"
date: 2009-11-13
forum: General Help
---

### Post by TitanTiger on 2009-11-13
I'm thinking about moving to Windows 7 on my Windows partition, but I'm not sure how to do this without messing up the boot loader or screwing up my Ubuntu install.  Is there a tutorial on doing this?

---

### Post by Eagles18 on 2009-11-13
> **TitanTiger said:**
> I'm thinking about moving to Windows 7 on my Windows partition, but I'm not sure how to do this without messing up the boot loader or screwing up my Ubuntu install.  Is there a tutorial on doing this?
Did you install it inside Windows?

---

### Post by TitanTiger on 2009-11-13
No, it's a dual boot set up, not with Wubi.

---

### Post by Eagles18 on 2009-11-13
> **TitanTiger said:**
> No, it's a dual boot set up, not with Wubi.
In that case it won't overwrite your Ubuntu because you'll be installing it over Vista or XP.

---

### Post by TitanTiger on 2009-11-13
What about the boot loader.

---

### Post by mikewhatever on 2009-11-13
The bootloader will be lost, but that's no biggie, you can reinstall it afterwards from the Ubuntu live cd. What version of Ubuntu is it,by the way?

---

### Post by TitanTiger on 2009-11-13
It's actually a variant of Ubuntu called Linux Mint.  It's based on 9.04.

---

### Post by mikewhatever on 2009-11-14
I see, but anyway, reinstalling GRUB should still work the same.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Ubuntu 9.10 has a newer, much canged version of GRUB with a different reinstallation procedure.

---

