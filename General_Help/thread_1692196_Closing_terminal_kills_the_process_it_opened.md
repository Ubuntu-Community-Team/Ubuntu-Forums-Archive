---
title: "Closing terminal kills the process it opened"
date: 2011-02-21
forum: General Help
---

### Post by kanishkdudeja on 2011-02-21
if i start an application using the terminal..

it gets closed if i close the terminal..

how can i not let this happen ?

---

### Post by gerowen on 2011-02-21
To my knowledge that's just the way it works, there's no real way around it.  If you open a program from the terminal the terminal you opened it with remains tied to the application and will spit out status and error messages.  If you just want to launch a program via the command instead of a GUI-fied shortcut, you can press Alt+F2 and type the command.  You can also add a "Run Command" button to the gnome panel.

---

### Post by Clever_Username on 2011-02-21
This should help
```
program [arguments] &
```

It runs the program in the background and returns you to a prompt. I believe you should be able to close your terminal window then.

---

### Post by gerowen on 2011-02-21
I withdraw my previous post, :p, learn something every day.

---

### Post by kanishkdudeja on 2011-02-21
thanks guys..:)

---

