---
title: "ssh &amp;&amp; ulimit"
date: 2009-10-02
forum: General Help
---

### Post by H4F on 2009-10-02
how do I restrict number of processes(ulimit) to user connected from ssh ?

---

### Post by Giblet5 on 2009-10-02
That's usually done via /etc/profile.

---

### Post by H4F on 2009-10-02
how do I do that in redhat ?

---

### Post by Giblet5 on 2009-10-02
> **H4F said:**
> how do I do that in redhat ?

The same way as in Ubuntu.

/etc/profile
or
/etc/bash.bashrc

```
man bash
```

Type "/ulimit" and read.

---

