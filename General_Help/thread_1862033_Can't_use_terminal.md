---
title: "Can't use terminal"
date: 2011-10-16
forum: General Help
---

### Post by Dd_rulez on 2011-10-16
Recently I haven't been able to install or just generally use terminal. I'm using Ubuntu 11.04 and if I go to install something ('sudo apt-get install xxxx)I enter my password but just get the message: 'Sorry, user dimitri is not allowed to execute '/usr/bin/apt-get install xxxx' as root on xxxxxxxxx.

Can anyone tell me what's wrong? 
Thanks for any help!

---

### Post by Lars Noodén on 2011-10-16
Are you in the group admin?

```

$ groups
thisuser adm dialout cdrom plugdev lpadmin admin sambashare

```

---

### Post by Dd_rulez on 2011-10-16
> **Lars Noodén said:**
> Are you in the group admin?

```

$ groups
thisuser adm dialout cdrom plugdev lpadmin admin sambashare

```

I'm not sure if I did this right but I got this:

```

groups
admin adm dialout fax cdrom floppy tape audio dip video plugdev fuse netdev lpadmin sambashare

```

So I guess that would be a yes, I am.

---

