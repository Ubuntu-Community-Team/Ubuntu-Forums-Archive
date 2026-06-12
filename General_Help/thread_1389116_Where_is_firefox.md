---
title: "Where is firefox"
date: 2010-01-24
forum: General Help
---

### Post by Bananasdoom on 2010-01-24
I am using thunder bird 3.0 and when I click on a link it asks me what program to open 
it with and then it opens up the file browser and well I don't have a clue where firefox is so please help. [IMG]http://img46.imageshack.us/img46/9853/54862262.jpg[/IMG]

---

### Post by nmaster on 2010-01-24
go to the terminal. 'which firefox' (without quotes) will tell you where it is.  

probably /usr/bin/firefox

---

### Post by efflandt on 2010-01-24
In a terminal:

efflandt@efflandt64-desktop:~$ **which firefox**
/usr/bin/firefox
efflandt@efflandt64-desktop:~$ **ls /usr/bin/firefox***
/usr/bin/firefox  /usr/bin/firefox-3.5

Actually /usr/bin should be in your path, so just plain **firefox** should run your default firefox (unless you want to run a specific version if you have more than one).

Or to see all files named firefox or in firefox directories try: **locate firefox | less** (press q to quit less)

---

### Post by nanotube on 2010-01-24
> **Bananasdoom said:**
> I am using thunder bird 3.0 and when I click on a link it asks me what program to open 
it with and then it opens up the file browser and well I don't have a clue where firefox is so please help. [IMG]http://img46.imageshack.us/img46/9853/54862262.jpg[/IMG]

well, firefox is in /usr/bin/firefox

EDIT: gah, too late! :)

---

### Post by Bananasdoom on 2010-01-24
Thanks heaps it worked a treat, I just went to** /usr/bin/** and searched for firefox and hey presto it worked THANKS !!!

---

### Post by feelshift on 2010-01-24
> **neal.m.master said:**
> go to the terminal. 'which firefox' (without quotes) will tell you where it is.  

probably /usr/bin/firefox

Learn a new trick every day :popcorn:

---

