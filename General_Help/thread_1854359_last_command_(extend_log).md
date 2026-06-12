---
title: "last command (extend log)"
date: 2011-10-04
forum: General Help
---

### Post by Drenriza on 2011-10-04
Hi all.

Does anyone know how you can extend the log that the last command uses.
So for example i can log every logon to a server for a month at a time.

Thanks on advance.
Kind regards.

---

### Post by Lars Noodén on 2011-10-04
**last** uses /var/log/wtmp, you can look in older sections of the log with **-f**. e.g.:

```

last -f /var/log/wtmp.1

```

and so on.

---

