---
title: "Why do I still have Shiretoko in Karmic 9.10???"
date: 2009-10-29
forum: General Help
---

### Post by dj-toonz on 2009-10-29
Hi all, I don't know what's happened, I thought Karmic 9.10 came with firefox 3.5.x but I've just taken a look at the about firefox on mine and it's saying 3.5.5pre?? 

here's a screenshot to prove it

---

### Post by dasunsrule32 on 2009-10-29
You should disable the repos for the pre-release versions of FF 3.5.x, in your /etc/apt/sources.list. Then do:

```
sudo apt-get remove firefox* \
&& sudo apt-get install firefox-3.5

```

That should take care of your issue with it.

---

