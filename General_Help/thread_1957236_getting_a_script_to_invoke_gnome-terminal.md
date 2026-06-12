---
title: "getting a script to invoke gnome-terminal"
date: 2012-04-12
forum: General Help
---

### Post by Thorsen V on 2012-04-12
is it possible to get a script to run gnome-terminal on the remainder of the script?

example:

```
#!/bin/sh

gnome-terminal -x find /home

```This opens the terminal, then closes when the listing ends (actually I'd like the terminal to stay open too).

But anything more elaborate than this doesn't seem to work, example:
```
#!/bin/sh

gnome-terminal -x find ~/Apps \; sleep 100

```With or without the escape the "sleep" doesn't occur.

The real script has a lot of conditional stuff and loops etc, so ideally I'd like a solution that doesn't destroy the formatting or require a second script file.

Possible?

---

### Post by cj13579 on 2012-04-12
Try quoting the gnome-term command. If you have any other quotes within that then these need to be escaped:

```
gnome-terminal -e "bash -c \"echo foo; echo bar; exec bash\""
```

The exec bash at the end is necessary because bash -c will terminate once the commands are done. exec causes the running process to be replaced by the new process, otherwise you will have two bash processes running.

Source: [http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution](http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution)

---

### Post by Thorsen V on 2012-04-12
> **cj13579 said:**
> Try quoting the gnome-term command. If you have any other quotes within that then these need to be escaped:

```
gnome-terminal -e "bash -c \"echo foo; echo bar; exec bash\""
```The exec bash at the end is necessary because bash -c will terminate once the commands are done. exec causes the running process to be replaced by the new process, otherwise you will have two bash processes running.

Source: [http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution](http://stackoverflow.com/questions/3512055/avoid-gnome-terminal-close-after-script-execution)
 
That did the  trick.

I shall make this as solved.

Thanks cj13579, much appreciated.

---

