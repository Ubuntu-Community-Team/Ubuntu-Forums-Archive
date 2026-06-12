---
title: "ubuntu won't boot with bash"
date: 2010-10-21
forum: General Help
---

### Post by gufide on 2010-10-21
Hi everybody, I've got a problem with bash, when I run my terminal or I turn into console mode, I get:
```
$
```

and I have to type "bash" and after I got:

```
master@comput1:~$
```

no one know how to make that bash alway running?

---

### Post by Brandon Williams on 2010-10-22
That sounds like you might not be configured to use bash as your default shell. Try running 'chsh', which will allow you to change your login shell. If it is not already '/bin/bash', then change it. If it's already /bin/bash, then there's something else going on here.

---

### Post by matt_symes on 2010-10-22
Hi

Sounds like you are running into dash and not bash.

chsh -s bash <username> (i think should work or some variation).

Kind regards

---

