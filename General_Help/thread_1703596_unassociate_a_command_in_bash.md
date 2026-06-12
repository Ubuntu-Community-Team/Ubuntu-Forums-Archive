---
title: "unassociate a command in bash"
date: 2011-03-09
forum: General Help
---

### Post by _AltF4_ on 2011-03-09
I uninstalled ubuntuzilla.py, with out any problems. However, if in bash I attempt to run ubuntuzilla.py it will inform me that: 
```
~$ ubuntuzilla.py
bash: /usr/local/bin/ubuntuzilla.py: No such file or directory
```while this isn't really an issue I was wondering how I unassociate ubuntuzilla.py with  /usr/local/bin/ubuntuzilla.py in bash.

---

### Post by tordeu on 2011-03-09
could you run this and tell me what it says:
```
which ubuntuzilla.py
```

Oh, and please run
```
alias ubuntuzilla.py
```
and post the output as well

---

