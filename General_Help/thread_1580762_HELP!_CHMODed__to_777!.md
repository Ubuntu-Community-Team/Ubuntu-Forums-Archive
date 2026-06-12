---
title: "HELP! CHMODed / to 777!"
date: 2010-09-23
forum: General Help
---

### Post by compiz addict on 2010-09-23
Umm. yeah... I meant to type "CHMOD 777 ." but i typed "CHMOD 777 /".

Is there a way to reverse this?

Is it safe to run a server in this state of insecurity?

---

### Post by Vaphell on 2010-09-23
did you do that with sudo and -R switch for chmod? if not, not much happened

```

ls -la /

```
check if there is stuff with rwxrwxrwx permissions

---

### Post by compiz addict on 2010-09-23
oh, ok. there are. So that means it's all good?

---

### Post by Vaphell on 2010-09-24
no, that's bad
you ran that chmod recursively?

---

