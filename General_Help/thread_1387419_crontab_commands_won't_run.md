---
title: "crontab commands won't run"
date: 2010-01-21
forum: General Help
---

### Post by Andante on 2010-01-21
**Edit:** commands like Firefox works after I set it to display properly. I still can't get personal scripts to run, though.

Hi everyone,

I can't seem to get crontab to run my commands. I add
```

* * * * * /home/username/script

```

but it doesn't seem to work. The script works itself in the shell.

Anyone know what's up? I'm running 9.10.

Thanks!

---

### Post by bluefrog on 2010-01-22
try 

* * * * * bash /home/username/script

---

