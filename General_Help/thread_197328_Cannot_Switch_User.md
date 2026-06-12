---
title: "Cannot Switch User"
date: 2006-06-15
forum: General Help
---

### Post by binjured on 2006-06-15
I am using XGL / Compiz right now and I cannot switch users.  Everytime I try it pops up an error stating "You do not seem to be logged in on the console.  Starting a new login only works correctly on the console".  What does this mean and how do I fix it?  Thanks :)

---

### Post by commonplace on 2006-11-26
I'm having this problem as well, using XGL and Beryl+Emerald. What's the fix for this?

/Kevin

---

### Post by hollerith on 2007-01-16
Arrgh!  Me too!  Beryl & Xgl

Do you get 'could not create server lock file /tmp/.X1-lock' too?

---

### Post by GZ1 on 2007-01-17
> **hollerith said:**
> Arrgh!  Me too!  Beryl & Xgl

Do you get 'could not create server lock file /tmp/.X1-lock' too?

Ouick fix for non-root ATI XGL: ```
chmod 1777 /tmp
```, then restart; although it  reverses sometimes (with crash?).

---

