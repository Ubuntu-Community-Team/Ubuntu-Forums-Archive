---
title: "kill not killing"
date: 2010-06-19
forum: General Help
---

### Post by punkbohemian on 2010-06-19
I'm teaching myself a little more about my os, so I'm toying around in the terminal using a web guide. Currently, I'm learning about the kill command. I started by running this command:

```

grep blank > filename

```

which should obviously never finish executing since "filename" doesn't exist. I run ps and get this:

```

  PID TTY          TIME CMD
15548 pts/0    00:00:00 bash
16013 pts/0    00:00:00 grep
18880 pts/0    00:00:00 ps

```

So far, so good. grep is there. I run "kill 16013" to kill it (without quotes, obviously), but ps generates the same output with grep still on the list. What's up with that?

---

### Post by rudy.b on 2010-06-19
Hi,

By default the kill command issues a termination request to the offending process which basically asks the process to shut itself down after doing all the proper cleanup.  If you find that isn't effective, you can issue a kill signal to terminate the process immediately:
```
kill -s 9 16013
```

---

