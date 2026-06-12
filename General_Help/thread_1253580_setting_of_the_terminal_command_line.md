---
title: "setting of the terminal command line"
date: 2009-08-30
forum: General Help
---

### Post by oren tal on 2009-08-30
currently when ever I launch terminal or when I get the terminal screen via ctl+alt+F1 it sometime show in what directory I am but not all the full path.

How can I make the command-line to display all the path of my directory.

I don't talk about using pwd but that I will see in the command line itself all the path to the directory that I am in.

---

### Post by Liolikas on 2009-08-30
Edit $HOME/.profile

---

### Post by oren tal on 2009-08-30
> **Liolikas said:**
> Edit $HOME/.profile
Thanks.
and what should I edit there (or maybe add)?

---

### Post by oren tal on 2009-08-30
sorry, but I don't have the file .profile  in my home directory.

---

### Post by oren tal on 2009-08-30
never mind.

My mistake, it does show me all the path.

---

### Post by NoaHall on 2009-08-30
You need to let hidden files to be shown (ctrl + h)

---

### Post by Liolikas on 2009-08-30
Here tutorial for **bash**, but you have **dash** but they are quite similar:
[http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/](http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/)

---

### Post by oren tal on 2009-08-30
> **Liolikas said:**
> Here tutorial for **bash**, but you have **dash** but they are quite similar:
[http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/](http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/)

thanks

---

### Post by oren tal on 2009-08-30
> **NoaHall said:**
> You need to let hidden files to be shown (ctrl + h)

thanks.

I did "ls -a" and it worked.

---

