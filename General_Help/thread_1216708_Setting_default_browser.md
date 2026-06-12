---
title: "Setting default browser"
date: 2009-07-18
forum: General Help
---

### Post by Alvaro_SG on 2009-07-18
Hi, yesterday I installed Ubuntu 9.04 (32-bit) and my favourite browser is Opera. I installed the latest snapshot v10 beta 2 (4433).

When I click on any tweetdeck link, it open Firefox but I need Opera.

How I can do it? Thanks.

---

### Post by michy99 on 2009-07-18
System->Preferences->Preferred Applications

---

### Post by wojox on 2009-07-18
System > Prefrences > Preferred Applications

---

### Post by Alvaro_SG on 2009-07-18
I did that, but no works.

---

### Post by Alvaro_SG on 2009-07-19
Please, help...

---

### Post by jrox717 on 2009-07-19
If preferred applications doesn't work, then maybe something in the appliction you're working on overrides that... look for preferred browser or something like that in tweetdeck?

---

### Post by VCoolio on 2009-07-19
You could also try 
```
sudo update-alternatives --config x-www-browser
```
and choose from the list. Or install galternatives to do it the gui way.

---

