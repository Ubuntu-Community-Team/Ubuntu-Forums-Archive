---
title: "figure out how part of a logfile got deleted"
date: 2011-01-19
forum: General Help
---

### Post by COKEDUDE on 2011-01-19
I there a way to figure out how part of a logfile got deleted? I know unix does not have a date created date so that makes things very difficult to tell if the file got deleted or not. Several thousand lines of my .bash_history somehow got deleted. I still have this in my .bashrc so I don't understand what happened.

```
HISTSIZE=9000 
```

---

### Post by wojox on 2011-01-19
See when it was last modified:

```
date --iso-8601=seconds -r .bash_history
```

---

### Post by COKEDUDE on 2011-01-19
> **wojox said:**
> See when it was last modified:

```
date --iso-8601=seconds -r .bash_history
```

How does that help me? Its the modified date. I can see that with **ls -l**. 

```
~ $ date --iso-8601=seconds -r .bash_history
2011-01-19T03:00:01-0500

```

---

