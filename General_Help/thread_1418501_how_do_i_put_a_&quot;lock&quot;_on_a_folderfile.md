---
title: "how do i put a &quot;lock&quot; on a folder/file?"
date: 2010-02-28
forum: General Help
---

### Post by sincerelyydavid on 2010-02-28
how do i put a "lock" on a folder/file?

---

### Post by asmoore82 on 2010-02-28
Right-Click => "Properties" and the "Permissions" Tab.

From there, you can set files to "Read Only" or directories to "Access Files[Only]"

---

### Post by falconindy on 2010-02-28
A stronger lock would be to set the immutable attribute (as you can still delete read-only if you own it):

```
chattr +i <target>
```

Unset it with -i.

---

