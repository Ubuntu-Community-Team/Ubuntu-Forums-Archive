---
title: "Could not login, desktop flashes 2 times, login again"
date: 2011-03-07
forum: General Help
---

### Post by iMPR3SSiON on 2011-03-07
Hi, I have a problem that prevents me from logging into my workstation. I have Ubuntu 10.10 up and running. Yesterday I reinstalled Nautilus, but during that it seemed like some important packages were gone. Restart and login screen, put in my password, screen goes black and flashes (like it could not find a driver or what not) 2 times and login screen appears again. 

I have googled quite a lot, tried to fix broken packeges, free up some space, but nothing seemed to work. In the worst case I can reinstall whole thing of course, but I do not want to do that. 

So if you have any ideas on how to solve it, I would be glad to read them. Thanks :)

---

### Post by Habitual on 2011-03-07
You can try this:
At the login GUI box:
```

Ctrl+Alt+F1
mv ~/.config ~/.config.org
mv ~/.gconf ~/.gconf.org
exit
```
Ctrl+Alt+F7 to login

Please let us know...

---

### Post by iMPR3SSiON on 2011-03-16
Well, thank you for your advice, problem was as simple as it could be ... I just installed 'ubuntu-desktop' package, which was uninstalled by my fault. Thank you again :)

---

