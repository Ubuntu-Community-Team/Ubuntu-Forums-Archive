---
title: "mount ISO without root"
date: 2010-04-05
forum: General Help
---

### Post by frt975 on 2010-04-05
How do I mount a ISO without root? There's my account that's admin and two others that don't have passwords or root privileges. I really hope its possible without having to edit /etc/fstab because that didn't help me because it mounted all the ISOs and I don't want to have to edit fstab every time I make a new ISO. I got the ISO by running ```
dd if=/dev/cdrom of=abc.ISO
```

---

### Post by SnickerSnack on 2010-04-05
Give the others enough sudo privileges to mount things?

---

### Post by KeyserSoze93 on 2010-04-05
Use fuseiso, just install it with aptitude or whatever (the package name is fuseiso.)

To mount:

```

mkdir ~/iso

fuseiso ~/my_iso.iso ~/iso

```

to unmount

```

fusermount -u ~/iso

```

---

### Post by frt975 on 2010-04-06
> **KeyserSoze93 said:**
> Use fuseiso, just install it with aptitude or whatever (the package name is fuseiso.)

To mount:

```

mkdir ~/iso

fuseiso ~/my_iso.iso ~/iso

```to unmount

```

fusermount -u ~/iso

```
Thanks! That's exactly what I'm looking for.

---

