---
title: "What's the difference: run program from rc2.d or from root command line?"
date: 2010-03-26
forum: General Help
---

### Post by lumix on 2010-03-26
Example:

In rc2.d I have S99test. In it:

```
#!/bin/sh
mplayer -playlist "/music/Thom Yorke - The Eraser"
```

Reboot; hear the loveliness; press pause (lirc setup)...still loveliness.

Login as root; "pkill mplay";hear nothing; "/etc/rc2.d/S99test"; more loveliness; press pause...silence!

I know that i the former case, mplayer is assigned (for lack of a proper term) to a session, e.g. tty1.  Not so in the latter.  But why should a program like mplayer not receive (or ignore?) input from lircd, simply because it doesn't have a session?

And how can I get mplayer (or any program run from boot scripts) to work with other programs (like lircd)?

---

### Post by lumix on 2010-03-28
Anyone?

---

