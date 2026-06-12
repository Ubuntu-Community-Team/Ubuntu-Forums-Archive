---
title: "The repository is not updated and the previous index files will be used.GPG error"
date: 2010-10-02
forum: General Help
---

### Post by peter27 on 2010-10-02
Hi,

I keep getting the following error when I run sudo apt-get update and it's driving me crazy:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://apt.spideroak.com](http://apt.spideroak.com) release Release:

NO_PUBKEY 5D654504F1A41D5E


Thanks in advance.

---

### Post by oldos2er on 2010-10-02
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5D654504F1A41D5E
```
assuming spideroak.com has a key on keyserver.ubuntu.com. If not, you might need to search their website for one.

---

