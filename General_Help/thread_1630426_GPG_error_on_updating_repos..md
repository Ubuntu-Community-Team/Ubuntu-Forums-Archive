---
title: "GPG error on updating repos."
date: 2010-11-25
forum: General Help
---

### Post by melrokz on 2010-11-25
This happened when I was reloading my repos using synaptic on Ubuntu 10.10.
How do I fix this?

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by wojox on 2010-11-25
Run these three commands in the terminal

```
gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192
gpg –export –armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```

---

### Post by plucky on 2010-11-25
> **wojox said:**
> Run these three commands in the terminal

```
gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192
gpg –export –armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```

The commands won't work.

Change the number from 3E5C1192 to 02FDF932 and also use -- in place of – in the commands.

Good Luck

---

