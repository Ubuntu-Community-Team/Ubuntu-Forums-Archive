---
title: "Why have another firefox package????"
date: 2006-06-06
forum: General Help
---

### Post by yusufm on 2006-06-06
I know that it might help distribute only compatible versions of firefox if their is an ubuntu package. But I don't think any future versions have a big risk of being incompatible.

I think ubuntu should de-couple itself from firefox, and let firefox update itself, since it already has a very good mechanism to do that. Since security fixes, etc. come out very fast by firefox directly.

This may also be something to consider with other well maintained packages that publish thier own updates...

---

### Post by frenkel on 2006-06-06
Letting firefox update itself wouldn't work, as you run firefox as a normal user. And normal users don't have write access in /usr normally. It would create a security hole to let users have write access in /usr.
What's wrong with apt-get update && apt-get upgrade?

---

### Post by yusufm on 2006-06-06
I don't want to use apt-get because the packages are not updated quickly. Firefox comes out with security fixes, etc. and the patches should be put in place as soon as possible. Does not help waiting days/weeks for ubuntu to update the repositories...

---

### Post by cleentrax on 2006-06-06
Letting Firefox upgrade itself destroys two of the primary ways in which Linux is better than Windows:

1. Integrated updates for every piece of software on the computer.
2. Increased security by restricting what applications can do.

Letting each application upgrade itself can cause dependency issues and open up security risks.

---

