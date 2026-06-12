---
title: "Change Username"
date: 2009-11-26
forum: General Help
---

### Post by rcastoro1 on 2009-11-26
Can I Change my Username to something else, post installation? Ubuntu 9.10. Is there any Risk Involved in disruption in file system if I do this?

---

### Post by raffaele181188 on 2009-11-26
The command is
```

usermod -l newname oldname

```
[This]("http://linux.die.net/man/8/usermod") is the man page. Note that you should also change the name of the home directory and maybe other things

---

### Post by Soul-Sing on 2009-11-26
> **rcastoro1 said:**
> Can I Change my Username to something else, post installation? Ubuntu 9.10. Is there any Risk Involved in disruption in file system if I do this?

this is not easily done, and rather complicated.

---

### Post by rcastoro1 on 2009-11-26
usermod is complicated?

---

### Post by Soul-Sing on 2009-11-26
> **rcastoro1 said:**
> usermod is complicated?

no, the possible negative implications for the/your op. system when changing your name.

---

### Post by rcastoro1 on 2009-11-26
Do you think it would be a good idea to just Create a New User with Administrative capabilities to mimic my current account with the new Username?

---

### Post by slumbergod on 2009-11-26
Yes

---

