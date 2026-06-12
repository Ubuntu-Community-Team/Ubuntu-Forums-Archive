---
title: "Non-root binding port below 1024"
date: 2006-02-24
forum: General Help
---

### Post by dmh-bidlah on 2006-02-24
Is there any way to let non-root users run programs that bind ports below 1024? I need Azureus to use port 113 to bypass my ISP-s firewall, but I don't want to run it as root.
If possible I would like to avoid recompiling the kernel, but if that is the only option...

---

### Post by heimo on 2006-02-24
Two paths I'd explore, authbind and port address translation (feature of net filter if I understand correctly).

authbind
> 
DESCRIPTION
authbind  allows  a  program  which does not or should not run as root to bind to low-numbered ports in a controlled way.


---

### Post by wirah on 2008-06-17
Has anyone got this to work yet?

authbind installs fine on my ubuntu, but I can't for the life of me get it to work!

Any ideas?

Cheers,

Antony

---

