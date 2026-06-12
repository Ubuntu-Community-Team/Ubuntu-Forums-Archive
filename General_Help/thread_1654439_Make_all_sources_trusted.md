---
title: "Make all sources trusted"
date: 2010-12-28
forum: General Help
---

### Post by ajukilibodin on 2010-12-28
Even though I followed every single step on "How to install from untrusted source" topic, i am still unable to install those applications. So my question is if there is a way that i can make all the sources trusted?

---

### Post by Spyderkid on 2010-12-28
if you've got the package somewhere saved do this to install them...

>Right click on the package
>go to permissions
>Put a tick in the box that says "allow executing file as a program"
>then you'll be able to install it.

Do this at your own risk.

---

### Post by dino99 on 2010-12-28
> **ajukilibodin said:**
> Even though I followed every single step on "How to install from untrusted source" topic, i am still unable to install those applications. So my question is if there is a way that i can make all the sources trusted?

Pray all the day long that maintainers dont forget about their packaging :)

then, press "ENTER" for breakage :)

---

### Post by ajukilibodin on 2010-12-28
Well, I am trying to install it from the Software Center. So, how does double click work on there?

---

### Post by oldos2er on 2010-12-28
Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` and post the output here?

---

