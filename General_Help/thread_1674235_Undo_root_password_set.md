---
title: "Undo root password set"
date: 2011-01-23
forum: General Help
---

### Post by Vimmander on 2011-01-23
Well, this is embarrassing.  I was trying to reset my personal account's password in Ubuntu (via the root prompt in recovery mode), and I typed

```
passwd
```instead of

```
passwd userNameHere
```#-o

How do I undo the password set for root?  From what I understand, it doesn't need a password, and I'm afraid I may have just ruined some built-in security feature that keeps root protected if you don't set a password.  I've got enough passwords to remember anyway...

---

### Post by mikewhatever on 2011-01-23
Check out the RootSudo documentation.
[https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account](https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account)
> sudo usermod -p '!' root

---

### Post by snowpine on 2011-01-23
See here: [https://help.ubuntu.com/community/RootSudo#Re-disabling](https://help.ubuntu.com/community/RootSudo#Re-disabling) your root account

---

