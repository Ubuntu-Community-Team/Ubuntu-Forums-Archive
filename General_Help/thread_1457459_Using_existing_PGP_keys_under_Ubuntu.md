---
title: "Using existing PGP keys under Ubuntu?"
date: 2010-04-18
forum: General Help
---

### Post by louis_mallow on 2010-04-18
When the new LTS releases I've decided to get rid of Windows from our main business box. The only thing stopping me right now is this: encryption.

I have lots of personal, pgp encrypted stuff, using the free non-commercial version. (Lots of personal financial and similar details I back up off-site.) 

Can anyone recommend packages that let me use my existing public/private key pairs to encrypt and decrypt .pgp files? I searched the repositories but can't see what to use.

---

### Post by dearingj on 2010-04-18
Take a look at [GnuPG]("apt://gnupg"). It can import and use most existing PGP keys.

---

