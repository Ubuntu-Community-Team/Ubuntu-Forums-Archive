---
title: "Help with Conky calendar"
date: 2009-08-17
forum: General Help
---

### Post by the_Ben on 2009-08-17
Howdy all,
I'd love to configure Conky so that the current date is highlighted.  Currently, I just have the generic calendar displaying.  I've scoured the net to the best of my ability, but have yet to come up with anything that works.  Suggestions?

---

### Post by the_Ben on 2009-08-26
That did it, thanks!  I only wish the author explained the code, but thankfully I understand enough to change the appearance.  Also, the method listed above removes the current month and year from being displayed.  I was able to amend this by adding:
```
${time %B %Y}
```

---

