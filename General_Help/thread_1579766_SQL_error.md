---
title: "SQL error"
date: 2010-09-22
forum: General Help
---

### Post by J V on 2010-09-22
I admit, it's been a while since I mucked with SQL, but what is wrong with this statement?
```
DELETE FROM comments, node, profile_values, users WHERE `uid` >5
```

> #1064 - You have an error in your SQL syntax; check the manual that  corresponds to your MySQL server version for the right syntax to use  near 'WHERE `uid` >5' at line 1

Or will it not let me delete seperate tables even though they share a common column?

---

