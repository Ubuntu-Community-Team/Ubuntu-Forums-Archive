---
title: "really quick CLI question"
date: 2009-11-09
forum: General Help
---

### Post by jazzvibes on 2009-11-09
Hi
Just want to know how to start a program running using the command line but then keep that terminal free to keep using. I think it's a suffix of a kind but I can't remember.

Example: I open a Terminal, and start bluetooth-applet. It comes up with all the stuff for the applet which I don't care about, I just want it to run, and then keep using the terminal. At the moment, if I close the terminal, the applet closes too ...

---

### Post by stylishpants on 2009-11-09
Append the ampersand (&) to your command to tell the terminal not to block while waiting for the command to run.

Redirect the output away with something like```
 >/dev/null 2>&1
```.

You can detach your process from the terminal with the 'disown' command to let you close your terminal without closing your running command as well.

Use 'jobs' to see a list of processes that are attached to your current shell, these are the ones that will get closed when your shell exits.  You can run 'help disown' to see more about how disown works, by default it will detach the most recently started process.

---

### Post by jazzvibes on 2009-11-09
cool works! Thanks

Just so I know what does the 2>&1 mean?

---

### Post by sisco311 on 2009-11-09
> **jazzvibes said:**
> cool works! Thanks

Just so I know what does the 2>&1 mean?

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html")

[http://tldp.org/LDP/abs/html/io-redirection.html]("http://tldp.org/LDP/abs/html/io-redirection.html")

---

### Post by t.rei on 2009-11-09
STDIN = 0 (input)
STDOUT = 1 (default output)
STDERR = 2 (default error-messages)

so in this case you redirect all output to /dev/null and "consider 2 the same as 1" (so basically make STDERR go the same way as STDOUT... down the drain).

---

### Post by Brian Vaughan on 2009-11-09
> **jazzvibes said:**
> cool works! Thanks

Just so I know what does the 2>&1 mean?

Output from "standard output" and "standard error" can be redirected from their default destination, basically the terminal screen.

In this case, "> /dev/null" redirected standard output to /dev/null, which is Unix for "nowhere." "2>&1" means to send standard error (2) to the same place that standard output (1) is going.

---

