---
title: "Oops"
date: 2011-08-15
forum: General Help
---

### Post by jmacx81 on 2011-08-15
I was trying to remove some KDE packages and once I did that nothing would open so I tried a reboot. Now I only can get to a terminal screen. Any ideas?

---

### Post by Bachstelze on 2011-08-15
Did you not remove ubuntu-desktop, by any chance? In the terminal, try

```
sudo apt-get install ubuntu-dekstop
```

---

### Post by ~!geek!~ on 2011-08-15
Just clicked on the quick post button and refreshed the page, which posted a blank reply to the post. 
Nevermind, above command must have been able to solve your problem.

---

### Post by jmacx81 on 2011-08-15
> **Bachstelze said:**
> Did you not remove ubuntu-desktop, by any chance? In the terminal, try

```
sudo apt-get install ubuntu-dekstop
```

I tried that and I get 
Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by cgroza on 2011-08-15
> **Bachstelze said:**
> Did you not remove ubuntu-desktop, by any chance? In the terminal, try

Ubuntu-desktop is just a meta-package. Removing it does not break anything.

---

### Post by jmacx81 on 2011-08-20
So I'm guessing my best bet would be to format the drive and re-install?

---

