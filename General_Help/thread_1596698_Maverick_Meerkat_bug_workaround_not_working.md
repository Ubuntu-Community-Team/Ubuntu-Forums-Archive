---
title: "Maverick Meerkat bug workaround not working"
date: 2010-10-14
forum: General Help
---

### Post by NewDisciple on 2010-10-14
Workaround for: &#65279;GPG Errors: If you get the following error message:
> W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used.
 GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
 
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)


&#65279;Run:

```
gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192
gpg –export –armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```

This did not work.  Another person had the same results and his comment was removed from the sticky. I hope someone has a working workaround for this.

---

### Post by kerry_s on 2010-10-14
just go into synaptic & reinstall "ubuntu-extras-keyring".

---

### Post by Mr_VeRiTy on 2010-10-14
> **kerry_s said:**
> just go into synaptic & reinstall "ubuntu-extras-keyring".
This did not work for me, I still get the same error.

---

### Post by NewDisciple on 2010-10-14
Thank you kerry_s, that did it.

---

