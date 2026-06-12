---
title: "What does this mean and how do i fix it?"
date: 2011-12-23
forum: General Help
---

### Post by mkstallings1 on 2011-12-23
I'm running 11.10 and recently, during an update, I got this message:


GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8520F66905311B6A

What does this mean and how do I fix it?

---

### Post by rubylaser on 2011-12-23
Apt-get guarantees the authenticity of the server before updating the system.  You just need to import the key into your keyring.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8520F66905311B6A
```

That should do it.

---

### Post by BC59 on 2011-12-23
Maybe you have to run this as well:

```
gpg --export --armor 8520F66905311B6A | sudo apt-key add -
```

---

### Post by mkstallings1 on 2011-12-24
Thanks!  That fixed it.

---

