---
title: "universal PATH setting in karmic"
date: 2010-04-02
forum: General Help
---

### Post by PlancksCnst on 2010-04-02
Where is the universal PATH variable set/exported in Karmic?

It is not exported from the normal place (/etc/profile). I can't find where it is set. I tried ```
find /etc/* | xargs grep "export PATH="
``` and it did not reveal the magic place.

---

### Post by geirha on 2010-04-02
/etc/environment

---

### Post by PlancksCnst on 2010-04-02
Hm... my /etc/environment is empty. I'll go ahead and put it there, but out of curiosity, where does PATH get set initially?

[update] Nevermind, I was ssh'd into another box when I looked at the file :oops:[/update]

---

