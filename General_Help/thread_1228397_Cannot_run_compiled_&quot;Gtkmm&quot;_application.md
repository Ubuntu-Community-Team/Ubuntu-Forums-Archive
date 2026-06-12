---
title: "Cannot run compiled &quot;Gtkmm&quot; application"
date: 2009-07-31
forum: General Help
---

### Post by petike on 2009-07-31
Hi all,
I have written a simple "Gtkmm" application and compiled it with this command:
```

g++ GtkmmApp.cpp -o GtkmmApp **-static** [COLOR=SeaGreen]**-Wl,-Bdynamic**[/COLOR] `pkg-config --cflags --libs gtkmm-2.4`

```It has compiled without problems but when I wanted to run it (by typing "./GtkmmApp"), I was given this message:
```

[COLOR=DarkRed]bash: ./GtkmmApp: No such file or directory[/COLOR]

```and nothing else happened.

When I tried to remove the **"-static"** flag from compiling parameters, then it ran without problems.
Does anybody know where is the problem?


[I]P.S.:
(The sense of **"-static -Wl,-Bdynamic"** flags is that I want only gtkmm libraries (or the whole list which "pkg-config" outputs) to be linked dynamically at runtime and "**EVERYTHING ELSE**" to be linked statically. By "everything else" I really mean everything else what the compiler needs to link to the executable)[/I]


Thanks.

---

### Post by petike on 2009-08-01
By the way,
on Windows (XP) it works fine also with the ***"-static"*** compiler option. Thus I can compile and also run it on Windows without problems.

Still no ideas?

---

