---
title: "startup script in foreground"
date: 2009-11-25
forum: General Help
---

### Post by loki_dre on 2009-11-25
Hello,

I am trying to add a startup script when the computer logs in.
I can get the script to run, but I can not see it.
How do I get it to run in the foreground?

I have added the script by going to "System"->"Preferences"->"Startup applications"

---

### Post by Findarato on 2009-11-25
What do you mean with "i cannot see it ?". A script is not supposed to be visible unless you have it display something.

---

### Post by Sam on 2009-11-25
To get the output of your script (assuming its a terminal application), run in gnome-terminal instead of directly:
```
gnome-terminal --command=/path/to/your/script
```

---

### Post by loki_dre on 2009-11-25
there is no GUI but i would like to see the standard output which is shown when i run it from a terminal.

eg.
echo HELLO WORLD

---

### Post by loki_dre on 2009-11-25
Thanks Sam

That worked!!!!
:p

---

### Post by Sam on 2009-11-25
You're welcome! ;)

---

