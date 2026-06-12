---
title: "Unknown Administrator Password"
date: 2012-01-19
forum: General Help
---

### Post by rushingad on 2012-01-19
The other day, I removed the login password from my administrator account, as well as changed the name, using the user accounts menu. Now when I try to do anything where it asks for authorization, it asks for a password, but the old one doesn't work, and leaving the field blank also doesn't work.

HELP

---

### Post by LinuxFan999 on 2012-01-19
Try re-adding the password.

---

### Post by CharlesA on 2012-01-19
> **rushingad said:**
> The other day, I removed the login password from my administrator account, as well as changed the name, using the user accounts menu. Now when I try to do anything where it asks for authorization, it asks for a password, but the old one doesn't work, and leaving the field blank also doesn't work.

HELP
How did you remove the login password?

---

### Post by rushingad on 2012-01-19
Can't unlock the user accounts menu to change anything.

I had gone to the user accounts menu and turned off the password at login, then went clicked on the password, and cleared it out.

---

### Post by Buntumatic on 2012-01-19
If you still have an account that can do sudo do ```
sudo -i
``` and set new password from CLI.

---

### Post by WorMzy on 2012-01-19
Is "the other account" a sudoer? If it is, you should be able to just reset the first accounts password with:

```
sudo passwd firstuser
```

Otherwise, use this:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

