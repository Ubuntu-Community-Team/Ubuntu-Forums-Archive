---
title: "Firefox Question."
date: 2010-02-18
forum: General Help
---

### Post by Roasted on 2010-02-18
Karmic comes with Firefox 3.5. I have a Firefox 3.6 PPA installed. If I want to go back to Firefox 3.5, what do I need to do? I was thinking remove the PPA, uninstall Firefox, then reinstall Firefox (which I would assume would grab it from the repo then). Is that train of thought correct?

---

### Post by epicoder on 2010-02-18
I believe so... I am assuming you mean something like:
```
sudo apt-get remove firefox-3.6
sudo apt-get install firefox
```

---

### Post by faical117 on 2010-02-18
Yes remove ppa and install firefox :KS

---

### Post by lovinglinux on 2010-02-19
Go to "System >> Administration >> Software Sources", disable the ppa and re-install Firefox.

---

### Post by Roasted on 2010-02-19
Thanks dudes, worked out nice.

---

