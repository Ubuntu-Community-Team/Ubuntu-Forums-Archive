---
title: "What replace the ksh buit-in whence?"
date: 2009-09-23
forum: General Help
---

### Post by samaricsm on 2009-09-23
**ksh** has a built-in program, *whence*, that tells you the absolute path to the file passed as an argument.  That does not seem to be part of **bash**.  Is there an equivalent function?

---

### Post by lloyd_b on 2009-09-23
> **samaricsm said:**
> **ksh** has a built-in program, *whence*, that tells you the absolute path to the file passed as an argument.  That does not seem to be part of **bash**.  Is there an equivalent function?

I believe you're looking for the "which" command (which is *not* part of bash, but rather an external command).  Note that "which" will NOT follow a symlink (for example, "/usr/bin/which" is a symlink to "/bin/which", but the command "which which" returns "/usr/bin/which").

Lloyd B.

---

### Post by Slim Odds on 2009-09-23
you can also use the bash builtin command 'type'

---

### Post by samaricsm on 2009-09-25
Thank you both.  Both command do what I was looking for.  I will close this thread.
Jim Hasslacher, Jr.

---

