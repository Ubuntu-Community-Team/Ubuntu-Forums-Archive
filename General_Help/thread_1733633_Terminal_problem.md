---
title: "Terminal problem"
date: 2011-04-19
forum: General Help
---

### Post by PCaddicted on 2011-04-19
It often happens that,If I paste a file in the terminal(or if I just type the path to it) and press Enter,I will get "No such file or directory".Do you have any explanation for this?
Also,I'd like you to reply to my unanswered threads if you can;their titles are:"Do not show window contents while dragging" and "Installed Gtkradiant on Ubuntu but it does not work".I am terribly sorry but I cannot give you the links,because I can't enable Javascript only for specific websites in the Opera browser that I am using,and I need Javascript to give you the links.Yet I do not want to enable Java,it would pose a security risk.Find my threads with the search function.
SO:Ubuntu 10.10

---

### Post by searchfgold6789 on 2011-04-19
It is likely that either the file does not exist, or you are typing the name in wrong. Here are a couple examples:
```
/                           # Root directory, equivalent to "C:/" in Windows
/home/richie                # My home directory
~/                          # The default directory, same as /home/richie
'/home/richie/tweak file'   # I had to begin and end this with a ' because the file name has a space in it.
/home/richie/.thunar        # This file is hidden and begins with a dot.
```

---

### Post by PCaddicted on 2011-04-19
Can anyone reply to my mentioned unanswered threads as well?
Also:that problem with the terminal will also occur even if I paste a file into the console!

---

### Post by searchfgold6789 on 2011-05-04
You could also click and drag the file into the terminal.

---

