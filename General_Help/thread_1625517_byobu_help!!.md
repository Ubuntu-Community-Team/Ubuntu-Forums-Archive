---
title: "byobu help!!"
date: 2010-11-19
forum: General Help
---

### Post by vinay nadig on 2010-11-19
hello, i wanted to autostart byobu when i started the terminal without having having to type byobu every time i started the terminal.

so i added the command to the .bashrc file in the last line.
the problem is that when i start the terminal, my system load goes through the roof and when i look at the system monitor, there are innumerable instances of bash opened, and eventually the system becomes unresponsive.
i cant figure out what the problem is.
any help would be appreciated.
thank you.

---

### Post by vinay nadig on 2010-11-23
bump
anyone???

---

### Post by nothingspecial on 2010-11-23
Depending on what you want, you could either

assign the command ```
gnome-terminal -x byobu
``` to whatever method you use to open a terminal (desktop icon, keyboard shortcut, menu entry).

Or, from byobu press F9 and set byobu to start at login

---

### Post by vinay nadig on 2010-11-23
thanx a bunch :D
that worked like a charm.
cheers!!



PS : the option to start byobu at login in byobu menu only works on the tty 1.
it is not working with the gnome-terminal(only on my system??  :-k ).

---

### Post by nothingspecial on 2010-11-23
> **vinay nadig said:**
> thanx a bunch :D




PS : the option to start byobu at login in byobu menu only works on the tty 1.
it is not working with the gnome-terminal(only on my system??  :-k ).

That`s why I said depending what you want ;)

---

### Post by Habitual on 2010-12-11
I know it says [SOLVED] but it got me going. 

Using nothingspecial's tip I came up with this.

Now I can connect to all my VMs using ssh in 1 click! (if they are running)
VMs that are NOT running, byobu will close those "windows".

I tried a few things, none worked.  Until this.

Open Terminal and run byobu-config and set up "Create New Windows" with this format:
**Title**: *Displayed Name* in byobu status line
**Command**: [I]ssh -t [email]user@domain.com[/email]
[/I]
and toggle down to Apply and hit Enter.

Now make a shell script with

```
#!/bin/bash
byobu-launcher
```

in it. chmod 700 /path/to/script.sh

Desktop launcher:
```
gnome-terminal -x /path/to/script.sh
```

Done.

Hope someone else gets something out of this. :)

---

