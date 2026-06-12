---
title: "Why is the &quot;history&quot; command not showing all recent commands"
date: 2010-08-08
forum: General Help
---

### Post by jeeves on 2010-08-08
When I type the "history" command I only get a list of **some** of the commands I typed recently. I have not cleared the history ( history -c ) recently, so its not a matter of it being flushed.

Anyone know why linux does this, and how I can get a complete list of recent commands?

---

### Post by luigi_mb on 2010-08-08
In .bashrc there should be the following two lines

HISTSIZE=500
HISTFILESIZE=1000

Change the numbers to suit, save, then restart the terminal.

/luigi

---

### Post by happyhamster on 2010-08-08
Also, commands that are preceded by whitespace characters won't be included in bash's history. (Will rarely happen when typing commands manually I suspect, but does sometimes occur when copying & pasting from a tutorial or such.)

---

