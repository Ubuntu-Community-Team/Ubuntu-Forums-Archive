---
title: "konsole history"
date: 2010-05-02
forum: General Help
---

### Post by jum1 on 2010-05-02
Hello
Im using Kubuntu 9.10 and the terminal Konsole
When I use the history, strange thinks happens

[upper arrow]
$ cd
[upper arrow]
$ sudo rm -rf linux-2.6.29.2/
[upper arrow]
$ **sudo rm -rf**cd ..
[upper arrow]
$ **sudo rm -rf**cat Documentation/

The part sudo rm -rf stays!! It happen quite often and it is very annoying for me.
does anyone has solved this problem ?
thanks

---

### Post by Untitled_No4 on 2010-05-02
Never had that problem and have just tried to rm -rf a file and see if it happens, but it does not.
Perhaps deleting your history will solve the problem? To do so you need to delete the ~/.bash_history file.

---

### Post by jum1 on 2010-05-02
> **Untitled_No4 said:**
> Never had that problem and have just tried to rm -rf a file and see if it happens, but it does not.
Perhaps deleting your history will solve the problem? To do so you need to delete the ~/.bash_history file.
this is just an example! it happen very often. Ill still try to delete the history file and tell you later if I encounter the problem again.

---

