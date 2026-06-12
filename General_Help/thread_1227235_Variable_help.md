---
title: "Variable help"
date: 2009-07-30
forum: General Help
---

### Post by Psycho.mario on 2009-07-30
I am creating a 4 character variable with:
> od -An -N2 -x /dev/random
How can i put a colon in the middle with a command?
e.g I have 7a6f and i want it to be: 7a:6f. How can i achieve this?

Thanks

---

### Post by SPr on 2009-07-30
```

od -An -N2 -x /dev/random|sed s/\ ../\&:/

```
The first character from the output of the od command is a space on Debian (ie the output is " 1234") so if Ubuntu is different (ie the output is "1234") use
```

od -An -N2 -x /dev/random|sed s/../\&:/

```

---

### Post by Psycho.mario on 2009-07-30
Perfect thanks, the first one works.

---

