---
title: "How to NOT show user, machine and directory on terminal"
date: 2011-10-22
forum: General Help
---

### Post by ataias on 2011-10-22
Hello there!

I'd like to make some changes in the normal visualization of linux terminal. Normally, it always shows:

ataias@ataias-notebook:~$ 

In other words, user, machine and the directory I am. I'd like to know how I change this, in a way it doesn't show directory, user or machine, only the $ or #. I tried to change terminal profile, but with no success.

Does anyone have an idea?

Regards

---

### Post by hwttdz on 2011-10-22
It's stored in your PS1 environment variable.

Try ```
export PS1=">"
```

There are all sorts of substitutions you can do, and you can actually be quite clever with it and have it display pretty nearly any information you want (in any color too!).

---

### Post by ataias on 2011-10-22
Thank you very much!

---

