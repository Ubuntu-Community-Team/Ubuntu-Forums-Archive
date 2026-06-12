---
title: "SSH only for users with admin privileges."
date: 2011-11-17
forum: General Help
---

### Post by MrWestwood on 2011-11-17
Is there any way to get ssh to only allow a user access via ssh if they are down as a system admin?

---

### Post by Lars Noodén on 2011-11-17
Yes.  Look at the configuration directive [AllowGroups](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html) and set that to "admin".

Or did you mean something more complex like allowing SSH and SFTP for only admin, but allow only SFTP for all others?

---

### Post by MrWestwood on 2011-11-17
That sounds like exactly what I want. I will give it a try tomorrow.

Many thanks for the speedy response.

---

