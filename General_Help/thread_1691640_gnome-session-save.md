---
title: "gnome-session-save"
date: 2011-02-20
forum: General Help
---

### Post by phanie on 2011-02-20
Hi again guys! Sadly, my last thread was not my second to the last thread as i have said there. So, here goes.

My problem is about gnome-session-save --force-logout. Well, it can be ran without any problems using the terminal or through a bash script. But when it is ran through UDEV and other remote ways of running it, it doesnt run. Is there a way to fix this? In UDEV, it posts an error whcih says 'Cannot open display' or something like that. Help me guys.

---

### Post by extraordinary_boy08 on 2011-02-20
There is actually a substitute for that terminal command. You can use 
```
skill -KILL -u <username>
```
This will not produce any error message especially when invoked remotely via ssh.

---

### Post by phanie on 2011-02-20
yea right..

---

