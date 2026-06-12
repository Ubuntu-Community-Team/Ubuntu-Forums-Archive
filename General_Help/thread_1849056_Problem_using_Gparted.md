---
title: "Problem using Gparted"
date: 2011-09-23
forum: General Help
---

### Post by jacatone on 2011-09-23
I'm using Ubuntu 10.04 LTS. Tried installing gparted but get the following error when I try launching it:

"jacatone@sony:~$ gparted
Inhibit all polling failed: Only uid 0 is authorized to inhibit the daemon"

Anyone know how to fix this? Thanks.

---

### Post by Ancanus on 2011-09-23
You need root permissions:

```

gksudo gparted

```

---

