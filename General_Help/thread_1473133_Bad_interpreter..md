---
title: "Bad interpreter."
date: 2010-05-04
forum: General Help
---

### Post by Namililith on 2010-05-04
Hello everyone. I am hoping someone can help me.

I was trying to install Webmin, and something went horrible wrong. When I startup I receive the following error:
```
-bash: /usr/bin/groups: /bin/sh: bad interpreter: No such file or directory
-bash: /usr/bin/lesspipe: /bin/sh: bad interpreter: No such file or directory

```

I am using Ubuntu 8.04 - 64 Bit. Can anyone guide me in correcting what I have done?

---

### Post by cariboo on 2010-05-04
The error message tells you what's wrong, check to make sure groups and lesspipe are installed, by opening a terminal and typing:

```
which groups
```

and

```
which lesspipe
```

---

### Post by Namililith on 2010-05-05
I should mention that I am remotely connected to the server via SSH.

It simply returns the same error that there is no such file. How would I go about reinstalling these?

---

