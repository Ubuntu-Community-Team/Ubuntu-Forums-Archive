---
title: "How to disable all output from a process? (&gt; /dev/null 2&gt;&amp;1 isn't useful)"
date: 2009-07-26
forum: General Help
---

### Post by Markhor on 2009-07-26
Hello. When I start firefox via a terminal :
    ```
 firefox index.html > /dev/null 2>&1 &
```
GLib-GObject-Warnings continue to flood the terminal screen.
Does anyone know how this can be prevented? Thanks

---

### Post by DaithiF on 2009-07-27
Probably not much help to you, but as far as i know the redirection above *should* work, and it does indeed work fine for me.  Maybe double-check that you are typing the command exactly as above?

a mistake sometimes made is with the ordering of the redirection parameters, so
someprogram 2>&1 > /dev/null & 
would not give the desired result because it first maps stderr to the terminal (which it already was anyway), and then redirects stdout to a file, leaving stderr still connected to a terminal.  But the way you have ordered it should give the desired result of both stdout and stderr being directed to /dev/null.

interested to hear if you figure this out

---

