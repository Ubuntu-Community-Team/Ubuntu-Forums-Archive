---
title: "samba mystery shares"
date: 2011-07-19
forum: General Help
---

### Post by AllGamer on 2011-07-19
Does anyone have an idea where else i can look up samba shares configuration that are NOT listed in the smb.conf?

some how these got created after playing around with GADMIN-SAMBA 

i've removed GADMIN-SAMBA and all its files and the shares are still there

i've went as far as removing samba then re-installing samba with fresh configuration and all, and those mystery folder shares comes back as soon as samba daemon is up.

---

### Post by Azdour on 2011-07-19
Hi,

Is there anything in /var/lib/samba/usershares?

---

### Post by AllGamer on 2011-07-19
indeed that was the issue
removed them all, and it's finally back to normal
thanks

---

