---
title: "How long sudo remembers the passwords?"
date: 2012-05-05
forum: General Help
---

### Post by deepaknet on 2012-05-05
When you issue a command prefixed with sudo it asks the elevated permissions password.

In the same terminal window, subsequent sudo commands don't seem to be asking the password repeatedly however out of the bolt I see the password prompt coming up.

So my question is whether it will count so many commands for the same authorization or some form of timeout governs?

---

### Post by hawkmage on 2012-05-05
The default is 5 minutes.  You can change it with the timestamp_timeout option of the Defaults in the sudoers file.

Take a look at the man page for sudoers.

---

