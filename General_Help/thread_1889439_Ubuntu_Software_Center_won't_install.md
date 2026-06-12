---
title: "Ubuntu Software Center won't install"
date: 2011-12-01
forum: General Help
---

### Post by nikeair on 2011-12-01
It worked for me at first and I installed a few applications but today it won't install anything.

Errors: Failed to download package files. Check your internet connection.

Requires installation of untrusted packages. The action would require the installation of packages from not authenticated sources.
Details, gelemental libelemental0 libgtkmm-2.4-1c2a

Any help would be greatly appreciated.

---

### Post by gennatolls on 2011-12-01
> **nikeair said:**
> Check your internet connection.
 Likely cause if NOTHING will install. Good luck

---

### Post by nikeair on 2011-12-01
I know my internet is working or I wouldn't be able to post on this forum as i look at these errors. :) It is something else.

---

### Post by gennatolls on 2011-12-01
Does it work if you:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Best of luck

---

### Post by nikeair on 2011-12-01
sudo apt-get update fixed it. Thank you very much for the help. :)

---

### Post by scarleo on 2011-12-01
Might be your mirror is down. Go to Software Sources and try another one or wait a while til yours gets back up.

---

### Post by gennatolls on 2011-12-01
Mirror was my next guess, glad your problem is solved.

---

