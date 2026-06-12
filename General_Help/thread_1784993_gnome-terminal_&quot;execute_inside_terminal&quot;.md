---
title: "gnome-terminal &quot;execute inside terminal&quot; when done everything closes"
date: 2011-06-17
forum: General Help
---

### Post by fixitdude on 2011-06-17
When I start gnome-terminal with either the -e or -x option, it says in the man page "Execute the remainder of the command line inside the terminal.".

Which to me would be like typing in a command, and when the command is done, it leaves the terminal window there and then you can type in another command.

Any ideas?

I also tried "gnome-terminal -x sh (then my command)", but as soon as the command ends it closes the gnome-terminal window. I also tried "&" to disconnect the command, no use.

---

### Post by Habitual on 2011-06-18
try ```
gnome-terminal -e "gedit"
``` as a "test". :)
Assuming (yeah, I know) you have gedit installed.
I get a terminal AND gedit. Close either one and they both close.

[http://pwet.fr/man/linux/commandes/gnome_terminal](http://pwet.fr/man/linux/commandes/gnome_terminal)

---

### Post by fixitdude on 2011-06-30
Just to be clear, I was hoping to have the terminal window stay open after a command is done.

---

### Post by Habitual on 2011-06-30
[http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution](http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution)

---

### Post by nothingspecial on 2011-07-01
Run bash, then the command, then bash again -

```
gnome-terminal -x bash -c "command; bash"
```

---

