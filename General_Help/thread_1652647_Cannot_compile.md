---
title: "Cannot compile"
date: 2010-12-25
forum: General Help
---

### Post by cd-r80 on 2010-12-25
Cannot compile?

warning: incompatible implicit declaration of built-in function ‘printf’


I have build-essential.

---

### Post by dino99 on 2010-12-25
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by cd-r80 on 2010-12-25
I didn't find answer there it says the same still:
"incompatible implicit declaration of built-in function."

---

### Post by matt_symes on 2010-12-25
Hi

What are you trying to compile?

Kind regards

---

### Post by WorMzy on 2010-12-25
That's a warning, not an error. The compiler shouldn't terminate there. Does it give any errors?

Is this an application you've written yourself? You may have forgotten to add some include statements to your source code (e.g. stdio.h). If it's not one you've written youself, you may want to contact the developer and let them know.

---

### Post by cd-r80 on 2010-12-25
Sorry, it compiled right. Even with errors.(warnings).

---

