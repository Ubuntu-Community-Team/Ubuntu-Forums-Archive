---
title: "How do I run a script in cron?"
date: 2010-07-10
forum: General Help
---

### Post by redfox1160 on 2010-07-10
How do I run a script in cron? would I do it like this:
```
* * * * * script.sh
```

---

### Post by mobilediesel on 2010-07-10
> **redfox1160 said:**
> How do I run a script in cron? would I do it like this:
```
* * * * * script.sh
```

Pretty close, you usually have to specify the path to the script unless it's within the PATH environment variable.

---

