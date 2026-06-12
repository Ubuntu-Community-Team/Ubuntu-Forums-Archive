---
title: "Launch for Command with Arguments"
date: 2009-09-24
forum: General Help
---

### Post by shaiss on 2009-09-24
I can launch
```
tsclient -x ~/.tsclient/backupsrv.rdp 
```
via terminal just fine.  Works 100%

But when I create a launcher with the same command it just launches tsclient.  My guess is its not passing the variables, I must be missing something small.

Thank you!:confused:

---

### Post by dcstar on 2009-09-25
> **shaiss said:**
> I can launch
```
tsclient -x ~/.tsclient/backupsrv.rdp 
```
via terminal just fine.  Works 100%

But when I create a launcher with the same command it just launches tsclient.  My guess is its not passing the variables, I must be missing something small.


There are various options available when creating launchers, try some of them.

---

### Post by geirha on 2009-09-25
The ~ gets expanded to your home directory in the shell, but the launcher does not expand that. Use the HOME environment variable instead
```
tsclient -x $HOME/.tsclient/backupsrv.rdp
```

---

### Post by arrange on 2009-09-25
Or use ```
bash -c "tsclient -x $HOME/.tsclient/backupsrv.rdp"
```

---

