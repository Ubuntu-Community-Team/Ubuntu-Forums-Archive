---
title: "Log in password unchanged, login keyring won't unlock"
date: 2010-08-21
forum: General Help
---

### Post by jpaugh64 on 2010-08-21
Hello. I have recently made a fresh install of Lucid Lynx. After restarting my computer (due to kernel updates), my log in password no longer unlocks my login keyring. I have never changed either password, so there is no "old" password to resort to.

How do I fix this? I am not opposed to deleting whatever data is encrypted by this keyring. Also, how might this have happened? This could be a bug; are there any relevant log files or such?

Much thanks.

---

### Post by borth92 on 2010-08-21
Try deleting the keyring, it will then ask you to set a new keyring.

Step 1: type the following (without the quotes) in a terminal: "rm ~/.gnome2/keyrings/default.keyring"

Step 2: Restart

---

