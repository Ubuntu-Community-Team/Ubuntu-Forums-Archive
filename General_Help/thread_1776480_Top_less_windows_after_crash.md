---
title: "Top less windows after crash"
date: 2011-06-06
forum: General Help
---

### Post by hakermania on 2011-06-06
Hello, once I closed an application and the PC stuck (i am strongly suspecting windows effects for this), then I pressed Ctrl+Alt+F1 to go to terminal and I restarted the pc through there.

Now,everything works fine, but, when the windows aren't maximised are topless (cannot drug them or close them). When they are maximized there is the global menu so there's no actual problem there.


Any possible solution for this and a suggestion on how to avoid future crashes like this?

Thanks.

---

### Post by pqwoerituytrueiwoq on 2011-06-06
windows are missing title bars right?
idk if this will work on kubuntu
but on ubuntu i do this
[FONT=Courier New]gtk-window-decorator &[/FONT]

---

### Post by hakermania on 2011-06-06
Ooops? Did I said kubuntu? By mistake!
Yes it worked like a charm!
Thanks!
Do you know how can I avoid future crashes?
It's he 3rd time the same thing happens!

---

### Post by prshah on 2011-06-06
> **hakermania said:**
> 
Now,everything works fine, but, when the windows aren't maximised are topless (cannot drug them or close them).

Too much adult nature and substance abuse messages on UF now :)

You can get back the title bar by pressing alt+f2 and giving the command ```
gtk-window-decorator --replace
```

It occasionally happens to me after an unclean shutdown. I don't know how to prevent it, but running this command always clears it up.

Please post back with your results.

---

### Post by pqwoerituytrueiwoq on 2011-06-06
try to figure out what caused it by looking into your log files 
open [FONT=Courier New]gnome-system-log[/FONT]

---

### Post by hakermania on 2011-06-07
> **pqwoerituytrueiwoq said:**
> try to figure out what caused it by looking into your log files 
open [FONT=Courier New]gnome-system-log[/FONT]

Eh, where exactly should I look in this flood of messages o.O?

---

### Post by hakermania on 2011-06-09
I figured out when the windows remain topless!
When I hit the combination
Alt+Space Bar

gtk-window-decorator exits with error:
```
** (gtk-window-decorator:19510): CRITICAL **: Could not find frame info \x98\xae\xfb\u0008\u0001 in frame type table
Segmentation fault
```

---

