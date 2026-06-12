---
title: "Do I have Ubuntu 9.04. or 9.10?"
date: 2009-12-28
forum: General Help
---

### Post by miros84 on 2009-12-28
Hello
i had Ubuntu 9.04
I upgraded some weeks ago, but I am not sure if everything was OK, and now I dont know if I have Ubuntu 9.04 or 9.10
How can I check it?

---

### Post by Shrek01 on 2009-12-28
Go to System > About Ubuntu

---

### Post by RobLikesBrunch on 2009-12-28
> **miros84 said:**
> Hello
i had Ubuntu 9.04
I upgraded some weeks ago, but I am not sure if everything was OK, and now I dont know if I have Ubuntu 9.04 or 9.10
How can I check it?

System --> About Ubuntu

Alternatively, you could do:

```
cat /proc/version
```

Or, to just get the kernel version:

```
uname -a
```

---

