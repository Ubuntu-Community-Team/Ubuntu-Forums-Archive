---
title: "compiz fusion"
date: 2011-09-24
forum: General Help
---

### Post by larjan on 2011-09-24
I recently did a clean install of 11.04. Downloaded approx. 9-23-2011. my previous install of 11.04, was from May 2011. There seems to be a pluggin missing from compiz, animation extras, that was there before. My question is , how do I get it? I have looked in the forums and googled it with no luck.

---

### Post by patryk77 on 2011-09-24
Open the terminal and run:
sudo apt-get update
apt-cache search compiz

Check if you aren't maybe missing one of the packages.

---

### Post by wildmanne39 on 2011-09-24
Hi, this should install all plugins for compiz.
```
sudo apt-get install compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins
```
and there is a guide in my signature with pictures for every step to set the cube and effect if you want too.
Thank you

---

### Post by larjan on 2011-09-25
Thanks, that did the trick. I appreciate the help very much.

---

### Post by wildmanne39 on 2011-09-25
Hi, your welcome! I am glad I could help.

---

