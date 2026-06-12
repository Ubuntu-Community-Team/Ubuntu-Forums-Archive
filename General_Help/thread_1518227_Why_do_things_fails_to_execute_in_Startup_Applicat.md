---
title: "Why do things fails to execute in Startup Applications"
date: 2010-06-26
forum: General Help
---

### Post by thecapsaicinkid on 2010-06-26
I want to start the program gm-notify.py on login, I add it to Startup Applications and it doesn't start. I run it from a terminal or alt-f2 run dialog and all is fine.

I try adding sleep 60 && gm-notify.py, still doesn't run on login.

I've tried created a script;

```
#!/bin/bash          

sleep 90
/usr/bin/gm-notify.py &

exit  
```..and calling that from Startup Applications and that doesn't work either.

Any ideas?

Thanks

---

### Post by Dysport on 2010-06-26
Have you tried something like "/usr/bin/python /usr/bin/gm-notify.py" ?

---

### Post by realzippy on 2010-06-26
+1,**python /usr/bin/gm-notify.py** should work.

---

### Post by thecapsaicinkid on 2010-06-26
That doesn't work yet I can open a terminal and execute just ```
gm-notify.py
``` and the notifier loads in the applet. Don't understand.

---

### Post by Dysport on 2010-06-26
I recall having a similar problem once. Though I don't remember how I solved it in the end. You could go ahead and try launching a terminal on startup which executes your command:
```
gnome-terminal -e "gm-notify.py"
```

---

### Post by thecapsaicinkid on 2010-06-26
> **Dysport said:**
> I recall having a similar problem once. Though I don't remember how I solved it in the end. You could go ahead and try launching a terminal on startup which executes your command:
```
gnome-terminal -e "gm-notify.py"
```
I'd tried that also, the terminal starts and then seems to quit after a second. Seems to be an issue starting python scripts at the point the Startup Applications commands are run maybe?

---

### Post by Dysport on 2010-06-26
What version of gm-notify are you using? Isn't there an option in the program itself that lets you choose to autostart?
Else I found a possible fix on[ launchpad]("https://bugs.launchpad.net/gm-notify/+bug/573555"): in /usr/share/applications/gm-notify.desktop comment out the line that says "#NotShowIn-GNOME;"

---

