---
title: "Seahorse Keyring Password"
date: 2009-08-22
forum: General Help
---

### Post by txwooley on 2009-08-22
My kids computer running 8.04 has multiple users on it.  Only my account has administrator priveledges and all three kids have limited privs.  I just set-up an e-mail account for my daughter using Evolution.  When she opens Evolution, it prompts for a Keyring password.  It will not accept the password she uses to log into her User, and will not accept my Administrator password either.  What is the default password for the Keyring?   Thanks in advance.

---

### Post by speedwell68 on 2009-08-22
> **txwooley said:**
> My kids computer running 8.04 has multiple users on it.  Only my account has administrator priveledges and all three kids have limited privs.  I just set-up an e-mail account for my daughter using Evolution.  When she opens Evolution, it prompts for a Keyring password.  It will not accept the password she uses to log into her User, and will not accept my Administrator password either.  What is the default password for the Keyring?   Thanks in advance.

IIRC the Keyring password is not necessarily the same as the Users password or the Root password.  It is whatever was entered when the Keyring manager prompted you to enter a password.

---

### Post by michy99 on 2009-08-22
While logged in to your daughter's account:```
rm ~/.gnome2/keyrings/default.keyring
```The next time she goes to use Evolution it should ask for a new password.

---

### Post by txwooley on 2009-08-22
> **michy99 said:**
> While logged in to your daughter's account:```
rm ~/.gnome2/keyrings/default.keyring
```The next time she goes to use Evolution it should ask for a new password.

That did the trick.  Thanks.  I'm not even sure who created the password let alone what the darn thing is! This did prompt for a new password, and she is happily e-mailing away as I type this.  Thanks for the help.

---

