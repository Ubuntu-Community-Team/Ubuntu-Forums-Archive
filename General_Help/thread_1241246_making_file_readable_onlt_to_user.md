---
title: "making file readable onlt to user"
date: 2009-08-15
forum: General Help
---

### Post by BufordPants on 2009-08-15
I am trying to make a .txt file readable/writeable/executable for a user.  I do not want anybody else to have access to the .txt file -- not even superuser.  How can I accomplish this goal?

---

### Post by Mardoct909 on 2009-08-15
Encrypt it. In Accessories make a key with the Passwords and Encryption Keys program. Use the key to sign the file, and thusly encrypt it, making it visible only to those with the passphrase and key. However, you'd have to decrypt it every time before use.

Also, you can try putting in a password protected .rar or something, but that's weak security.

---

