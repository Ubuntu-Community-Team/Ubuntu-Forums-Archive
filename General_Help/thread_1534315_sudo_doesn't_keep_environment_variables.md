---
title: "sudo doesn't keep environment variables"
date: 2010-07-19
forum: General Help
---

### Post by JordyD on 2010-07-19
When I execute something with sudo, the environment that it executes in doesn't have all the environment variables from /etc/profile{,.d/} defined.  I googled around and found that there is a way to get the environment variables from the calling environment to be carried over to sudo's own environment, but that's not exactly what I want.  I just want sudo to read the /etc/profile and /etc/profile.d/ before executing commands.

If anyone could help me with this, it would be appreciated.

Thanks,
Jordy

---

### Post by gmargo on 2010-07-19
Try the -i option to simulate initial login.

---

### Post by JordyD on 2010-07-19
> **gmargo said:**
> Try the -i option to simulate initial login.

That did it. Thanks. :)

---

