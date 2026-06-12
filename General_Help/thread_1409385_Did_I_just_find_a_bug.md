---
title: "Did I just find a bug?"
date: 2010-02-17
forum: General Help
---

### Post by robofighter on 2010-02-17
I had a .sh file to load for sun virtualbox's guest addons.
When I first clicked on it it said I needed admin rights to continue.

So what I did is right click and used "open with", and created a custom command called "gksudo." I opened it and I expected to see that menu popup asking for my password.

But when I then open that shell script. It did not ask me for my password and when ahead and installed it.

---

### Post by mk1w86 on 2010-02-17
You might have entered your password beforehand for something else and your account rights were still elevated. :-k

---

### Post by robofighter on 2010-02-17
come to think of it, I was having updates being install at that time.

Is that what caused it?

---

### Post by sisco311 on 2010-02-17
Once a user has been authenticated, a timestamp is updated and the user may then use sudo/gksu without a password for a short period of time (by default, 15 minutes).

---

### Post by geirha on 2010-02-17
Likely. gksudo checks how long it has been since last you successfully used gksudo, and if it's less than 15 minutes (I think), it won't bug you for a password.

---

