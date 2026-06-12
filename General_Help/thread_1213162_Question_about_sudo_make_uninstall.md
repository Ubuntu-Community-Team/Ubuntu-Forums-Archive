---
title: "Question about sudo make uninstall"
date: 2009-07-14
forum: General Help
---

### Post by kogger on 2009-07-14
This is a really stupid question, but for some reason I can't figure this out.

I was messing around with creating programs using gtkmm and make, and I created a basic hello world-style program that I tested installing with make, and then with sudo make install. Everything worked as I expected, and then I uninstalled it with sudo make uninstall.

But for some reason the name of my executable ('hello') is still tied to the directory that make install put it in (/usr/local/bin). When I type in 'hello', instead of getting "bash: hello: command not found", I get "bash: /usr/local/bin/hello: no such file or directory". Even if I create another executable with the same name and place it higher on the search path, my computer now requires any command with the name 'hello' to be in that directory.

I'm sure there's a configuration option somewhere specifying this that make install put and make uninstall failed to remove...but I have no idea where it would be. Anyone know how to fix this?

---

### Post by michy99 on 2009-07-14
Perhaps install created an alias for hello=/usr/local/bin/hello

---

### Post by kogger on 2009-07-14
Where would that have been saved, though?

---

### Post by kogger on 2009-07-14
...bump?

---

### Post by kogger on 2009-07-14
Well. Logging out and in again seems to have worked.

---

