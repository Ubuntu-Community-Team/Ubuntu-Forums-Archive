---
title: "Repository Error on Ubuntu 9.10"
date: 2010-01-14
forum: General Help
---

### Post by weaver4 on 2010-01-14
Adding repository error.

When ever I try to do this:

**'sudo  add-apt-repository ppa:xorg-edgers/ppa'**  that is a 'colon and a x' there not a smiley face.

I get this error.

[B]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 165D673674A995B3E64BF0CF4F191A5A8844C542
gpg: requesting key 8844C542 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0[/B]

---

### Post by Cheesemill on 2010-01-14
I think the key server is down at the moment, there are a few people with the same problem.

---

