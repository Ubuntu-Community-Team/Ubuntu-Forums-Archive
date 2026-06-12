---
title: "Power Monitor Off Command"
date: 2010-11-21
forum: General Help
---

### Post by simonthecat on 2010-11-21
Where is the command that the system uses to power a monitor off for power saving mode?

Also how can I define a new action in the Keyboard Shortcuts program that will point to a script?

Thank you for your help.

---

### Post by dcstar on 2010-11-21
> **simonthecat said:**
> Where is the command that the system uses to power a monitor off for power saving mode?

Also how can I define a new action in the Keyboard Shortcuts program that will point to a script?

Thank you for your help.

```
man xset
man setterm
```

---

### Post by simonthecat on 2010-11-22
Thank you dcstar. From xset I got:
xset dpms force standby
Which does just what I want!

Setterm though seems to set parameters within the terminal. I'm thinking of the keyboard shortcuts within gnome. I'm unsure from the man page how I would use this command to do this.

---

### Post by dcstar on 2010-11-23
> **simonthecat said:**
> Thank you dcstar. From xset I got:
xset dpms force standby
Which does just what I want!


Then read below:

---

