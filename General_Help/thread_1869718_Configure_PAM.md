---
title: "Configure PAM"
date: 2011-10-26
forum: General Help
---

### Post by Lorens on 2011-10-26
Hi everyone!

I'm trying to configure gmd linux-pam to login on a radius server.

I have already installed and configured libpam-radius-auth.

Making the firts tests I have notice, taking a look on the radius servers logs, that the password is a hash.

So the question is, how can I configure PAM to not hash the password?

Thanks in advance.

---

### Post by Lorens on 2011-11-10
It was a stupid mistake, the SECRET at pam_radius_auth.conf was not correct...

---

