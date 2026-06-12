---
title: "how to exit help (man &lt;command&gt;) in terminal mode?"
date: 2011-04-24
forum: General Help
---

### Post by sandorvonv on 2011-04-24
I just installed Ubuntu 10.10 on a Dell Dimension 4600C (500MB RAM, 40GB HD). I have some previous experience with HP-UX, and wanted to try Linux on the desktop primarily to "play" with shell scripts in Terminal mode. When entering any "man <topic>" command, I am not returned to command line, even if the man page has reached END.  CTRL-C does not work. I can only put the man process in background (CTRL-Z) , which "jobs" shows as "Stopped". I then have to kill it (kill %1). "echo $TERM" shows xterm; do i need to change it to vt100? and if so, how?
Thanks in advance ... av

---

### Post by WorMzy on 2011-04-24
Press q.

---

### Post by Vaphell on 2011-04-24
Q

---

### Post by RJ12 on 2011-04-24
As everyone else said, pressing "q" will quit the man page and return you back to the shell prompt.

---

### Post by sandorvonv on 2011-04-24
duh! ... thanks! ... and thanks for not laughing at me

---

