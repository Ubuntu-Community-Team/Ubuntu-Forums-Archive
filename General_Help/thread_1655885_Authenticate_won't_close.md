---
title: "Authenticate won't close"
date: 2010-12-30
forum: General Help
---

### Post by Ali Kante on 2010-12-30
Hi folks,  I'm having a problem with the authentication window, if I want to change  system properties. There are two buttons cancel and authenticate, but  nothing happens when I push authenticate.   Any ideas?:confused:

---

### Post by sisco311 on 2010-12-30
Hi, 

It's a known bug: [lpbug]649939[/lpbug]

It's fixed, but the package is not available from the official repositories. You have to install polkit-1 (0.96-2ubuntu1.2) from: [https://launchpad.net/~james-w/+archive/polkit](https://launchpad.net/~james-w/+archive/polkit)

```
sudo add-apt-repository ppa:james-w/polkit
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Ali Kante on 2011-01-01
Great. Thanks!

---

### Post by Loevborg on 2011-01-10
I was bitten by the same bug. Thanks for posting this.

---

### Post by sprintexec on 2011-03-29
I don't know why I put up with the authenticate problem for so long! Anyway, thanks for the solution! AJ:guitar:

---

