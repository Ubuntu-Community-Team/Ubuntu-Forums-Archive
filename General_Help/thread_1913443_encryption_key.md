---
title: "encryption key"
date: 2012-01-22
forum: General Help
---

### Post by brain7734 on 2012-01-22
Hi, everybody! Would removing the 'password and encryption key' app be OK, or is this not recommended? I have auto login (I'm the only one who uses this computer), but after startup this 'key' comes up saying some program needs permission to do *something *(can't remember). Can I uninstall without it wrecking the computer?

---

### Post by sanderd17 on 2012-01-22
> **brain7734 said:**
> Hi, everybody! Would removing the 'password and encryption key' app be OK, or is this not recommended? I have auto login (I'm the only one who uses this computer), but after startup this 'key' comes up saying some program needs permission to do *something *(can't remember). Can I uninstall without it wrecking the computer?

Normally, your wireless network will stop working when you remove it.

---

### Post by mcduck on 2012-01-22
> **sanderd17 said:**
> Normally, your wireless network will stop working when you remove it.

...as will any other program that needs the keyring to store some information. I wouldn't recommend doing that...

Anyway, there's a better solution that solves the problem, just set the keyring password to empty one and you won't get asked for it any more, but the applications will still be able to use the keyring.

To do that open the Password and Encryption Keys, then right-click the "Passwords:login"-keyring and select "Change Password". Type in the old password but leave the fields for new one empty. You'll get a warning that this will make the keyring store data in unencrypted format, but since you are using an automatic login anyway it doesn't really make any difference security-wise.

---

