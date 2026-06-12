---
title: "No space left on device during kernel update on btrfs"
date: 2011-11-21
forum: General Help
---

### Post by Yahoé on 2011-11-21
11.10 amd64.
A kernel update just got pushed but it won't complete returning an error message:
"dpkg : erreur de traitement de /var/cache/apt/archives/linux-headers-3.0.0-13-generic_3.0.0-13.22_amd64.deb (--unpack) :  impossible d'installer une nouvelle version de « /usr/src/linux-headers-3.0.0-13-generic/include/linux/i8042.h »: Aucun espace disponible sur le périphérique
Aucun rapport « apport » n'a été créé car un disque plein a été signalé
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/linux-headers-3.0.0-13-generic_3.0.0-13.22_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)".

There's a lot of free space available on this btrfs compressed partition so the problem is elsewere. I read a couple post about similar problems, but nothing conclusive.

Any help would be appreciated.

---

### Post by dunkirk on 2011-11-24
Just here to say it's happening to me trying to install 11.10 on btrfs. I'll also add that I'm being forced into btrfs because ext4 seems to be having problems with my SSD. If I can't try this to see if it fixes the problem, Ubuntu is essentially dead to me. Back to Gentoo? I shudder.

---

### Post by Yahoé on 2011-11-24
I reported this as bug #893681, you can subsribe to it. Let hope they'll move one this quickly.

---

