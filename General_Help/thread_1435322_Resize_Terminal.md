---
title: "Resize Terminal"
date: 2010-03-21
forum: General Help
---

### Post by txwooley on 2010-03-21
I am writing an application that runs in terminal and re-sizes it using
```
resize -s 30 90
```
That works just fine.  So now I create a .desktop file to add this app to the applications menu.  So far so good.  But when I run the app from the menu, the terminal doesn't resize and it claims
```
can't open terminal /dev/tty
```
So I added a line to have the tty identify itself.  Terminal claims it is not a 'tty'.  So how do I get my terminal to re-size from the menu like it does when I just open a terminal and enter the name of the app?  I really want to keep the .desktop file so I can re-distribute this app to some friends who are still pretty new to Linux and want pointy-clicky stuff.

---

### Post by geirha on 2010-03-21
Make sure the launcher type is «Application in Terminal» and not just «Application». Otherwise it won't run the script in a terminal.

---

