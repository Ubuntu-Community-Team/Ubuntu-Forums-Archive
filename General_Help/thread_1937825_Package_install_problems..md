---
title: "Package install problems."
date: 2012-03-08
forum: General Help
---

### Post by dagroves on 2012-03-08
I am trying to install the .deb for 4Shared Cloud Storage. When I do I get an error. So I open up Synaptic and I get the same error. Check out the screenshot below. What do I do?

---

### Post by dagroves on 2012-03-08
Nevermind, I solved it. But for those who need the answer, I did this in a terminal:
```

sudo dpkg --remove --force-remove-reinstreq 'name-of-package'


```

---

