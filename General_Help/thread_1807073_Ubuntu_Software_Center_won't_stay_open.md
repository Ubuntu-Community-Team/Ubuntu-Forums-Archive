---
title: "Ubuntu Software Center won't stay open"
date: 2011-07-18
forum: General Help
---

### Post by PsyclonJohn on 2011-07-18
Hello, it was just yesterday when I was using the Ubuntu Software Center, and it worked great. Today, when I open it, it closes right down within a second.

If it helps, I'm using Ubuntu 10.04.

I restarted Ubuntu, the problem still happens, anyone know what could be causing this?

---

### Post by jerrrys on 2011-07-19
have you tried reinstalling it?

sudo apt-get remove software-center
sudo apt-get install software-center

---

### Post by plucky on 2011-07-19
> **jerrrys said:**
> have you tried reinstalling it?

sudo apt-get remove software-center
sudo apt-get install software-center

Before doing that,open a terminal and post output of ```
sudo apt-get update && sudo apt-get upgrade
```

---

