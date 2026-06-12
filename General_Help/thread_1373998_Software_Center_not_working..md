---
title: "Software Center not working."
date: 2010-01-06
forum: General Help
---

### Post by SanjogS on 2010-01-06
It opens, I can choose the software I want to install but when I click install nothing happens.

---

### Post by philinux on 2010-01-06
> **SanjogS said:**
> It opens, I can choose the software I want to install but when I click install nothing happens.

Open a terminal. Apps>accessories>terminal. Copy and paste this in and press enter. It will ask for your login password.

```
sudo apt-get update && sudo apt-get upgrade
```

Post back any errors.

---

### Post by SanjogS on 2010-01-06
Aint working. :(

Is that Owen Coyle in your Avatar?

---

### Post by philinux on 2010-01-06
> **SanjogS said:**
> Aint working. :(

Is that Owen Coyle in your Avatar?

Yep it is. I'm changing it soon as he's off to Bolton. Shame

Cant help unless we see the error messages that code spits out.

---

### Post by howefield on 2010-01-07
Try installing from the terminal,

```
sudo apt-get install packagenamehere
```

Then post back any errors/success.

---

