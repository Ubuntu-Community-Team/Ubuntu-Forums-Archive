---
title: "Permissions - Writing Files In Different Default Permission."
date: 2010-05-10
forum: General Help
---

### Post by Roasted on 2010-05-10
Currently when I create a folder, it comes down as 755 permissions.

I want it to come down as 775 permissions by default.

How can I change this?

---

### Post by dcstar on 2010-05-10
> **Roasted said:**
> Currently when I create a folder, it comes down as 755 permissions.

I want it to come down as 775 permissions by default.

How can I change this?

Change the umask in either ~.profile (user) or /etc/profile (system default).

---

### Post by Roasted on 2010-05-10
Hm, is it possible to adjust the umask to just ONE folder in the entire system? Or does this change it system wide?

I guess when I make a folder and set the permissions to 775, to me logic would suggest that whatever I create inside would take on 775 permissions OR there would be an easy option to allow it to do so. Instead it's the opposite. Blah. 

Thankfully there are Samba options to take care of this "fault", but I'd really like to be able to do this on the local system so I don't have to worry about changing write permissions for the group with every file I move locally.

---

