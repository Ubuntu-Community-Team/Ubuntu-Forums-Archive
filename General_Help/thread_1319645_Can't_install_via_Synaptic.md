---
title: "Can't install via Synaptic"
date: 2009-11-08
forum: General Help
---

### Post by serpicolugnut on 2009-11-08
New install of Ubuntu 9.10 (x86). Trying to install some items through synaptic and apt-get in the terminal, and I'm unable to. I get this msg through Synaptic:

> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Does anyone know how to rectify this?

---

### Post by zvacet on 2009-11-09
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mthalis on 2009-11-09
Raead this [http://ubuntuforums.org/showthread.php?t=1236282](http://ubuntuforums.org/showthread.php?t=1236282)

---

### Post by MelDJ on 2009-11-09
add the gpg key by trying the link in my sig

---

