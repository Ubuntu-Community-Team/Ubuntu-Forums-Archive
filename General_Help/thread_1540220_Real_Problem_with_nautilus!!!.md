---
title: "Real Problem with nautilus!!!"
date: 2010-07-27
forum: General Help
---

### Post by hakermania on 2010-07-27
This seems very embarrassing!!!
Times to times nautilus "stacks" and needs force quit.
I had posted this problem here some months before and no solution was found. Before 1 month I installed 10.04 and I had exactly the same problem. One day, after nautilus stacked I run an app that pings google. Then I opened up an other terminal and typed
killall -v ping
Then, not one but 2 ping apps were killed. Means that an other ping app was running!!!
After I gave the kill ping command I opened up a nautilus window and worked fine!

From then till now I know that when nautilus stacks if I give
killall -v ping
it will unstack.

This solves the problem but is quite embarrassing too....
WHY IS THIS PING DONE?
WHY WHEN IT IS DONE NAUTILUS STACKS?
Please help me!

---

### Post by hakermania on 2010-07-28
Ok, this is really serious and somebody has to reply!
I am feeling like spies are into my PC.!

---

### Post by dragos240 on 2010-07-28
Hello. Try deleting the .nautilus directory in your home folder by doing this:
rm -rf .nautilus

---

### Post by hakermania on 2010-07-28
For what reason to do this? The directory is empty
```
alex@MaD-pc:~/.nautilus$ ll
total 8
drwxr-xr-x  2 alex alex 4096 2010-05-15 22:04 ./
drwxr-xr-x 74 alex alex 4096 2010-07-28 12:11 ../
alex@MaD-pc:~/.nautilus$
```

---

### Post by hakermania on 2010-07-28
Even if I do force-quit and then type
killall -v ping
nautilus continues running normally and rebuilds the desktop

---

### Post by prodigy_ on 2010-07-28
Do you use sshfs by any chance? Or any other kind of network file system? For me Nautilus usually hangs if a server shuts down while its file system is still mounted with sshfs.

---

### Post by hakermania on 2010-07-28
No, no... I don't use anything like this. nautilus freezes in moment you didn't expect to do so, and always that time a 'ping' process begin to ping [www.google.com](www.google.com). I kill this process and then nautilus works as it should to..

---

### Post by hakermania on 2010-07-29
Plzzz... Can anyone help me????????

---

