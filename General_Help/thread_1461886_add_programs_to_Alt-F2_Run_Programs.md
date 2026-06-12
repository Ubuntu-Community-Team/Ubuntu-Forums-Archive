---
title: "add programs to Alt-F2 Run Programs"
date: 2010-04-24
forum: General Help
---

### Post by Timothy Benton on 2010-04-24
I downloaded the latest Chromium build but to run it I have to go into its folder and click it, or I can type its full address ( /home/ubuntu/chrome-browser/chrome ). I want to be able to hit Alt-F2 and type just "chrome" How can I add the program to the list of shortcuts?

Also I would like to disable the saving of history in Alt-F2

---

### Post by Kljuka on 2010-04-24
I guess you also can't launch it from the terminal typing chrome? It's not in one of directories where path links to.
Try creating a symbolic link in /usr/local/bin/ to chrome
```
ln -s /usr/local/bin/chrome /home/ubuntu/chrome-browser/chrome
```

---

