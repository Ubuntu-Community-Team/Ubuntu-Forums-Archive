---
title: "What's wrong with my crontab?"
date: 2009-11-30
forum: General Help
---

### Post by sprince09 on 2009-11-30
I have a script that I want to run every 30 minutes. My crontab looks like:


```

30 * * * * /absolute/path/to/python_script.py

```

I know the script works, but the scrip never executes under cron except when I first boot up my laptop. What gives?

---

### Post by andrew.46 on 2009-12-01
Hi sprince,

> **sprince09 said:**
> 
```

30 * * * * /absolute/path/to/python_script.py

```


Perhaps try:

```

**[COLOR="Red"]*/[/COLOR]**30 * * * * /absolute/path/to/python_script.py

```

All the best,

Andrew

---

### Post by sprince09 on 2009-12-01
No luck :(

---

