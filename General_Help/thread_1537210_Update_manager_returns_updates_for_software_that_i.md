---
title: "Update manager returns updates for software that isn't installed"
date: 2010-07-23
forum: General Help
---

### Post by culfunius on 2010-07-23
Hello, my update manager has run today and returned updates for firefox. Which would be a superb, immensely handy thing - if firefox happened to be installed on my box. It isn't.

Why does the update manager return updates for software that isn't installed? And how can I stop it from doing so?

---

### Post by bluntknife on 2010-07-23
Is it definitely a software update and not a software recommendation?

Did you used to have firefox installed?

---

### Post by culfunius on 2010-07-23
It's in with the security updates. I've had to change the frequency of update checks to once a week because I'm quickly getting tired of unchecking the firefox updates each day.

Firefox was installed with the default ubuntu installation. Preferring Chrome, I remove --purge'd it afterwards.

---

### Post by pricetech on 2010-07-23
Possibility:
Some of Firefox's files meet dependencies for something else, which makes Update Manager want to update it ??

---

### Post by culfunius on 2010-07-23
If it is a dependency elsewhere, how could i find out what? I really don't want to have to download the firefox application every time it updates if it isn't even installed.

---

### Post by philinux on 2010-07-23
> **culfunius said:**
> If it is a dependency elsewhere, how could i find out what? I really don't want to have to download the firefox application every time it updates if it isn't even installed.

Probably xulrunner. Which I think chromium needs anyway.

---

### Post by culfunius on 2010-07-25
> **philinux said:**
> Probably xulrunner. Which I think chromium needs anyway.

I'd already approved the xulrunner upgrade - it comes separately. 

I think the totem plugin for FF may have been the culprit. I've removed it.

---

