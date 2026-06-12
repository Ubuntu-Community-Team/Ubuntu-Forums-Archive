---
title: "Skype-does it work well with 10.04?"
date: 2010-09-03
forum: General Help
---

### Post by dogdo on 2010-09-03
I seem to recall older versions of skype being rather buggy with linux-is this still the case?

---

### Post by coolman98 on 2010-09-03
no skype now is pretty stable.

---

### Post by dogdo on 2010-09-07
Just a quick question-

I have the first account on my laptop(the account installed at installation) and it can use skype. I also have another account (desktop user-not a admin account) that cant use skype. So does that mean skype needs sudo access?

---

### Post by 3Miro on 2010-09-07
SKYPE DOES NOT NEED SUDO! Do not run such software with sudo, some people say you shouldn't run skype as the default user either.

Go to the second user's account and try to start skype from the terminal (Apps -> Accessories -> Terminal) and see if you get an error message. Only start the program with:
```
skype
```
and no sudo.

---

