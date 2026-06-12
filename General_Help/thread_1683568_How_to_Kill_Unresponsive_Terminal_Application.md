---
title: "How to Kill Unresponsive Terminal Application?"
date: 2011-02-07
forum: General Help
---

### Post by Wardrop on 2011-02-07
I just ran "mysqld" manually in the terminal, but now I can't quit it and go back to bash. I've tried CTRL+C and typing "reset", but neither do anything. Anything I type is just ignored.

I've had this numerous times in the past with various operating systems and in various scenario's, hence why I'm seeking the solution. Is there some universal hotkey to quit the currently running application or something?

I guess I'm looking for a way to send SIGQUIT, SIGTERM or possibly even a EOF signal?

Cheers

---

### Post by Wardrop on 2011-02-07
I found this web page which was somewhat helpful: [https://wiki.archlinux.org/index.php/List_of_Keyboard_Shortcuts](https://wiki.archlinux.org/index.php/List_of_Keyboard_Shortcuts)

In the process of trying those hotkeys however, I've accidentally hit Windows Key + \ (backslash), which threw me back into bash. This seems to be the magical quit kotkey I'm after, but haven't managed to find any info on it. Does anyone know what the Windows key does in Linux (or Ubuntu), and what Windows Key + \ actually does?

---

### Post by JLangford on 2011-02-07
Press alt + F2 to bring up the run dialogue, then type 'xkill' then click the window you wish to kill, should close it immediately.

EDIT: Never mind, didn't take into account that you're in the terminal.
On second thoughts the xkill command may still work, but I don't know.

---

### Post by Wardrop on 2011-02-07
Yeah, xkill didn't work.

---

### Post by Habitual on 2011-02-08
Ctrl+Shift+T = new tab.

Use the Red X button to close the first one.

Assumes gnome-terminal. Sorry.

---

