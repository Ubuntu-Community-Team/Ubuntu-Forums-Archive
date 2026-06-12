---
title: "How can I get Seahorse Passwords and Keys to read-in passwords from $HOME/.gnupg?"
date: 2012-08-22
forum: General Help
---

### Post by GeoffreyBernardo on 2012-08-22
After reinstalling my system, I copied the .gnupg folder from backup into my new home folder.

  Unfortunately, Seahorse does not read-in the passwords from that folder.

  It does pick-up the ssh keys from the .ssh folder and the certificate keys from .gnupg.

  With a previous reinstall, it did pick-up the passwords.

---

### Post by GeoffreyBernardo on 2012-08-23
Seahorse does not read the passwords from **$HOME/.gnupg**, but from **$HOME/.gnome2/keyrings**.

---

