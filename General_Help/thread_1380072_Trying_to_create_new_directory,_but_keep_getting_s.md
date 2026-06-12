---
title: "Trying to create new directory, but keep getting same error."
date: 2010-01-13
forum: General Help
---

### Post by smiich on 2010-01-13
Hey, I'm trying to create a new directory using the mkdir command. 

```

home@ubuntu:~$ mkdir <aicoursework>
bash: syntax error near unexpected token `newline'

```

that's the error that i keep getting, what am i doing wrong?

---

### Post by philinux on 2010-01-13
> **smiich said:**
> Hey, I'm trying to create a new directory using the mkdir command. 

```

home@ubuntu:~$ mkdir <aicoursework>
bash: syntax error near unexpected token `newline'

```

that's the error that i keep getting, what am i doing wrong?

You cannot use < or > in a directory name unless you do it like this

```
mkdir "<blah>"
```

---

### Post by smiich on 2010-01-13
oh thanks! and how would you delete said directory?

---

### Post by philinux on 2010-01-13
> **smiich said:**
> oh thanks! and how would you delete said directory?

Right click then "move to deleted items folder".

---

### Post by david819 on 2010-01-13
> **smiich said:**
> oh thanks! and how would you delete said directory?

rmdir

---

### Post by smiich on 2010-01-13
thank you

---

