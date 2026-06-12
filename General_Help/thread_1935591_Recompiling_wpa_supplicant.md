---
title: "Recompiling wpa_supplicant"
date: 2012-03-04
forum: General Help
---

### Post by 4techx on 2012-03-04
hi all,

i have come across a solution to a problem i am having which i am afraid is a little too technical for me to make sense of. the actual advice which i found on another forum is:

"Recompiling the wpa_supplicant package against GNUTLS seems to solve the issue".

i was hoping someone could please explain to me exactly how i would go about doing this, as it has all gone completely over my head. 

if anybody would like a link to the original thread, it is [here]("https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/429370"). thanks guys.

---

### Post by MG&amp;TL on 2012-03-04
From the same thread: [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/429370/comments/21]("https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/429370/comments/21")

If you want help with some of that, post back. :)

---

### Post by TeoBigusGeekus on 2012-03-04
When compiling, add this
```
$(pkg-config --cflags --libs gnutls)
```
line to the gcc command.

---

### Post by 4techx on 2012-03-04
i must apologise,,, i can't believe i didn't see that the process had already been explained!

---

### Post by MG&amp;TL on 2012-03-04
> **4techx said:**
> i must apologise,,, i can't believe i didn't see that the process had already been explained!

No problem at all, happens to all of us!

---

