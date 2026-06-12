---
title: "Can't get any updates!"
date: 2010-09-07
forum: General Help
---

### Post by Ehknaton on 2010-09-07
This is a serious problem! 
I just did a **clean instalation** of **Xubuntu** and I can't update. I think there is something wrong with the repositories. 
Previously i had **ubuntu** and that didn't update either, even after fiddling with source.list. The **internet is working** fine. 
What's wrong?

---

### Post by plucky on 2010-09-07
Open a terminal and post output of ```
cat /etc/apt/sources.list
```

What does it say if you run from the terminal window ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```

---

