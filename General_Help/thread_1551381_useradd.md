---
title: "useradd"
date: 2010-08-12
forum: General Help
---

### Post by fdelval on 2010-08-12
Hello, i just did:

useradd john -d /home/john
mkdir /home/john
passwd john


now, from other pc, i used john to connect via ssh.

Its weird because with my initial ubuntu iser i see this in command line:

frank@ubuntuser:~$

now, with john i only see:

$



and not just that, but i cant use the TAB to autofill things like /et(TAB) -> /etc

what am i missing?

---

### Post by Bachstelze on 2010-08-12
```
sudo chsh -s /bin/bash john
```

Default shell in Ubuntu is dash.

---

### Post by fdelval on 2010-08-12
> **Bachstelze said:**
> ```
sudo chsh -s /bin/bash john
```Default shell in Ubuntu is dash.

Hello Bachstelze, you are very active and helpfull, thank you.

2 questions:

A) Besides the differences i pointed out, are there other differences?? not being able to exe scripts or...

B) i didnt modified the default used i created when i installed ubuntu, which means doesnt belong (or shouldnt ) to any group, neither this user does
Would you make any further config about the new user¿??

---

