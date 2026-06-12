---
title: "sshfs command in launcher with password-protected private key?"
date: 2010-07-13
forum: General Help
---

### Post by lightnb on 2010-07-13
I'd like to connect to a site via the sshfs command from a launcher on the task bar. The problem is, instead of prompting for the password for my private key (key based authentication), the launcher freezes the computer.

The command runs fine from the terminal... but is there a way to add a password prompt to a launcher?

---

### Post by lightnb on 2010-07-30
bump.

---

### Post by prodigy_ on 2010-07-30
Should work from a launcher too. At least the following works for me: ```

sshfs user@host:/ /media/mountpoint -o allow_other,default_permissions
```
I get a GUI password prompt when I try to connect.

---

