---
title: "Scrot...."
date: 2012-04-10
forum: General Help
---

### Post by saders on 2012-04-10
hello all,


 need help- i have installed scrot in one of the ubuntu system the logs always save in home folder which is pretty obvious now here the thing i want- i want to save these logs in my other computer which is connected through lan or how can i block users to acces admin-home folder(but the logs must be coming) so if anyone have any answers please let me know

thanks in advance...

---

### Post by Hubi17 on 2012-04-11
Hi

From what I understand you want to move the screenshots taken with scrot to a different folder.
I use the following command

```
scrot -e 'mv $f ~/entertainment/pictures/screenshots/ 2>/dev/null'
```

I guess if you want to copy them to a remote machine then you would have to use scp?

---

### Post by cariboo on 2012-04-12
Moved to General Help, as this question has nothing to do with security.

---

