---
title: "script issue"
date: 2010-10-02
forum: General Help
---

### Post by U_buntu on 2010-10-02
I wrote two scripts, linking one to the other, but as I am testing all the commands out, once I am connected to the 2nd script and prompt for exit, it takes me back the the first script (which I do not want to do). On top over taking me back to the first script, the options work, but are not listed. I just have to know which option and the correct response. Is there a way to exit the 2nd script without being brought back to the first script?

---

### Post by lloyd_b on 2010-10-03
> **U_buntu said:**
> I wrote two scripts, linking one to the other, but as I am testing all the commands out, once I am connected to the 2nd script and prompt for exit, it takes me back the the first script (which I do not want to do). On top over taking me back to the first script, the options work, but are not listed. I just have to know which option and the correct response. Is there a way to exit the 2nd script without being brought back to the first script?

By default, calling a second script (or command) from within a shell will execute that script/command, and then return to the caller.

If you want it to execute that script, and never return, then instead of just using the script name, use the "exec" command:```
exec somecommand
```This tells the shell to replace the current process, instead of spawning a new one, and will not return to the caller.

Lloyd B.

---

### Post by U_buntu on 2010-10-03
Awesome, thanks alot. this one was giving me lots of problems.

Btw, like your signature.

---

