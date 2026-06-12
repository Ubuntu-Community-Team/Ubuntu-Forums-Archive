---
title: "force quit Force Quit?"
date: 2010-09-24
forum: General Help
---

### Post by ellebanna on 2010-09-24
So I have force quit and the little window is stuck. reads "click on a window to force the application to quit. To cancel press <ESC>"

How the heck do I get rid of it? I tried xkill, it does not work.

---

### Post by Rocket2DMn on 2010-09-24
Are you able to kill the app from System->Administration->System Monitor?

Otherwise you need to get the process id and kill it from the command line
To show a list of all running processes:
```
ps -ef
```
Then kill the process:
```
kill *pid*
```
e.g.
```
kill 12345
```

---

### Post by Ocxic on 2010-09-24
Did you hit "esc"?? (lol)

---

### Post by ellebanna on 2010-10-09
> **Rocket2DMn said:**
> Are you able to kill the app from System->Administration->System Monitor?

Otherwise you need to get the process id and kill it from the command line
To show a list of all running processes:
```
ps -ef
```
Then kill the process:
```
kill *pid*
```
e.g.
```
kill 12345
```

Thanks, I shall have to try this next time it goes poopy.  Thankfully this is the least of my compie issues.

Ocxic. . .While I admit I am not much more than your basic computer user, would I even know what Ubuntu was if I was not that computer literate?

---

