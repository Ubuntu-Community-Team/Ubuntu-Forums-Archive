---
title: "Error during apt-get update..."
date: 2009-09-28
forum: General Help
---

### Post by zakie-chan on 2009-09-28
Im trying to do an update but it returns these errors:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release amd64 (20090121)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release amd64 (20090121)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


Any help would be much appreciated as im not very good with command line...


Zakie

---

### Post by zvacet on 2009-09-29
Applications>accessories>terminal and type (or can copy/paste)

```
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

That will sort medibuntu.For other thing just uncheck CD as repository.Look[here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

