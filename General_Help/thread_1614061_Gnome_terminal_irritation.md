---
title: "Gnome terminal irritation"
date: 2010-11-05
forum: General Help
---

### Post by mixmaster on 2010-11-05
The gnome terminal has taken to querying me every time I exit:

> 
Close this terminal?

There is still a process running in this terminal. Closing the terminal will kill it.

This is because there is an unclosed ssh session in the window.  I am quite happy for the system to close this silently (as it has been doing until my update to 10.10) but I can't see how to turn off the prompt.

Any ideas or do I go back to xterm?

---

### Post by Barriehie on 2010-11-06
> **mixmaster said:**
> The gnome terminal has taken to querying me every time I exit:



This is because there is an unclosed ssh session in the window.  I am quite happy for the system to close this silently (as it has been doing until my update to 10.10) but I can't see how to turn off the prompt.

Any ideas or do I go back to xterm?

How about an alias, or a script, that closes the ssh session and then kills the terminal too?

---

