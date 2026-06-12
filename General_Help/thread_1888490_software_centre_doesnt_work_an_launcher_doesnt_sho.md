---
title: "software centre doesnt work an launcher doesnt show apps"
date: 2011-11-29
forum: General Help
---

### Post by sirvinniei on 2011-11-29
having the exact same problem noted here [http://askubuntu.com/questions/70647/ubuntu-software-center-freezes-with-an-introspect-error?s=22873182-3c9d-4b83-8b83-cdab638ce419#new-answer](http://askubuntu.com/questions/70647/ubuntu-software-center-freezes-with-an-introspect-error?s=22873182-3c9d-4b83-8b83-cdab638ce419#new-answer)
does anyone know what to do?

---

### Post by sirvinniei on 2011-11-29
Bump

---

### Post by sirvinniei on 2011-11-29
bump, plz anyone?

---

### Post by raja.genupula on 2011-11-29
issues seem different to me , but giving a try is not at all bad.

```
sudo apt-get install --reinstall software-center
```

---

### Post by sirvinniei on 2011-11-29
> **raja.genupula said:**
> issues seem different to me , but giving a try is not at all bad.

```
sudo apt-get install --reinstall software-center
```
still the same error and just now it booted but froze

---

### Post by sirvinniei on 2011-11-29
found something interresting:
when i try sudo software-center in terminal it works but otherwise it doesnt

---

### Post by raja.genupula on 2011-11-29
hmmm ok man clean install of software will make it fresh i think 

go with this 

```
sudo apt-get remove --purge software-center
sudo apt-get install software-center
```

all the best.

---

### Post by sirvinniei on 2011-11-30
nevermind, today the dash and the softwarecenter apparently work correctly

thanks anyway

---

### Post by raja.genupula on 2011-11-30
glad to hear that , welcome !

---

