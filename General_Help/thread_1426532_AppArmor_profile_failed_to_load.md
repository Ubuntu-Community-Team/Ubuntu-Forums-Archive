---
title: "AppArmor profile failed to load"
date: 2010-03-10
forum: General Help
---

### Post by Mardok45 on 2010-03-10
I'm running Ubuntu server 9.10 and am trying to load a Xen kernel, but it's giving me this error message:
```

Warning: unable to find a suitable fs in /proc/mounts, is it mounted?
Use --subdomainfs to override.
Failure: AppArmor profiles failed to load
Done.

```

And it just pauses there.

Does anyone know how to get the proper AppArmor profile for that Xen kernel (or whatever it is I need to do)?

EDIT: Just to clarify, I downloaded the Xen kernel from a Debian FTP server.  Is there something in the repository that I need to install so AppArmor will quit complaining?
I downloaded linux-modules-2.6.26-2-xen-amd64_2.6.26-21_amd64.deb and linux-image-2.6.26-2-xen-amd64_2.6.26-21_amd64.deb.

---

### Post by klausner on 2010-06-12
> **Mardok45 said:**
> I'm running Ubuntu server 9.10 and am trying to load a Xen kernel, but it's giving me this error message:
```

Warning: unable to find a suitable fs in /proc/mounts, is it mounted?
Use --subdomainfs to override.
Failure: AppArmor profiles failed to load
Done.

```

And it just pauses there.

Does anyone know how to get the proper AppArmor profile for that Xen kernel (or whatever it is I need to do)?

EDIT: Just to clarify, I downloaded the Xen kernel from a Debian FTP server.  Is there something in the repository that I need to install so AppArmor will quit complaining?
I downloaded linux-modules-2.6.26-2-xen-amd64_2.6.26-21_amd64.deb and linux-image-2.6.26-2-xen-amd64_2.6.26-21_amd64.deb.

Same problem with Lucid.

---

### Post by klausner on 2010-06-15
Bump!

---

