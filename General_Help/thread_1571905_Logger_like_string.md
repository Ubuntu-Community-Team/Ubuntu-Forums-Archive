---
title: "Logger like string"
date: 2010-09-10
forum: General Help
---

### Post by dragos2 on 2010-09-10
I want to output an entry to a log file similar to what logger produces.

"Sep  9 20:37:40 server user: service started"

How to construct such a string in a simple way ?

---

### Post by ubulal on 2010-09-10
What programming language?

If you want to append to one of the existing log files in /var/log I would strongly recommend using the official interfaces, i.e. logger(1) for shell scripts or syslog(3) for C programs.

---

### Post by dragos2 on 2010-09-10
> **ubulal said:**
> What programming language?

If you want to append to one of the existing log files in /var/log I would strongly recommend using the official interfaces, i.e. logger(1) for shell scripts or syslog(3) for C programs.

I want to add some logging to a bash script.

I can do it with date, awk and env but it does not look very pretty.

---

### Post by ubulal on 2010-09-10
> **dragos2 said:**
> I want to add some logging to a bash script.

If your message is to be appended to an existing system log, use logger(1)!  That way you get the standard formatting for free.

Otherwise:
```

echo `date "+%b %e %T"` server user: service started >> logfile

```

---

