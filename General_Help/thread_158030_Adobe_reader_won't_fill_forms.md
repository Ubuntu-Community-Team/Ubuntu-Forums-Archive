---
title: "Adobe reader won't fill forms"
date: 2006-04-10
forum: General Help
---

### Post by drpaul on 2006-04-10
I just installed the Adobe reader with Automatix. This version complains about missing Javascript plugin and doesn't see any of the fields in a form. Can this be fixed? Do I have to go back to a version 5?

TIA

Paul

---

### Post by Al3xanR0 on 2006-04-10
[QUOTE=drpaul]I just installed the Adobe reader with Automatix. This version complains about missing Javascript plugin and doesn't see any of the fields in a form. Can this be fixed? Do I have to go back to a version 5?

TIA

Paul[/QUOTE]

I'm not 100% sure but I think what you need is the jre 1.4 (java runtime env) see if that does the trick.. Or you may need to creat a symlink of the plugin lib to the mozilla plugin dir. These forms that you are attemptingt to view, are they on line or locally stored?

---

### Post by greenpenguin on 2006-04-10
I dont think Java being installed would help you here... I would suggest installing adobe reader by hand.

---

### Post by drpaul on 2006-04-10
Right. The form is local. It has nothing to do with browser [Firefox]. Do you think I should install the 7.0.5 or the 5.0?

Paul

---

### Post by drpaul on 2006-04-10
Aha! Solved the problem by installing the Ubuntu acroread plugin package even though it is only 7.0.1.  The acroread is 7.0.5 or 7.0.7.  Thanks for the help.

Paul

---

### Post by jbuberel on 2006-11-23
Just to be clear - the package you need to install is named:

```
acroread-plugins
```

Not to be confused with the mozilla/firefox acroread plugin :D

---

