---
title: "partial upgrade from development version - refuses"
date: 2010-05-09
forum: General Help
---

### Post by peter_kint on 2010-05-09
Hi,
I'm currently running Lucid (development branch) dual booting with Vista.

```
peter@peter-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"
```I still need Windows for specific software that doesn't exist for Linux.
Everything works fine.

1. The Update Manager pops up, suggesting me to upgrade.
2.At the same time he pops up another window telling me I can only do a partial upgrade (because of various reasons)
3. I get this error message
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
4. When I tell him to go ahead with this 'partial upgrade', he starts calculating for 10 minutes and then tells me he cannot upgrade at all!

QUESTIONS:
-Do I need to upgrade? (I'm afraid to mess up, now that I have everything working)
-I suspect I have to do a clean install of the most recent Ubuntu, instead of trying to upgrade?
 If so, how do I do that? Burn a disk with the iso-file?
-Will he install it over my current Ubuntu?
-Can I keep dual-booting with windows (I've seen many issues on this forumt with GRUB loaders and Windows partions disappearing..). I still need Windows for specific software that doesn't exist for Linux.

If necessary, I'm willing to do a clean install but I want to be sure to be able to dual boot.
Maybe someone can point out pitfalls/issues for me?

Thx

---

### Post by peter_kint on 2010-05-10
bump

---

### Post by peter_kint on 2010-05-12
bump

---

### Post by ibuclaw on 2010-05-12
How did you try to upgrade the system?


It looks like you have a Debian repository in your sources lists which is invalid. Open up 'Software Sources' (In System -> Administration) and remove / untick it.


Regards

---

### Post by peter_kint on 2010-05-12
> **ibuclaw said:**
> How did you try to upgrade the system?


It looks like you have a Debian repository in your sources lists which is invalid. Open up 'Software Sources' (In System -> Administration) and remove / untick it.


Regards

Thx a lot,
That did the trick.

Regards,
PK

---

