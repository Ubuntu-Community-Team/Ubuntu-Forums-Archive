---
title: "spaces in file names - terminal?"
date: 2011-04-16
forum: General Help
---

### Post by javajames97 on 2011-04-16
Im in terminal, and say i want to run a file called; 'Tic Tac Toe'    but terminal reads: do 'tic' to tac and toe??? Then im in gedit, and i want to edit a text file called 'hello world', so i enter: 'gedit hello world', but terminal reads: 'gedit hello and gedit world', thus opening 2 new tabs in gedit. To put this plain and simply, i have file names (and app names) with 2 or more words in  them - with spaces as seperation. I cant use these because terminal BASH doesn't read them how i want them to be read, how would i go about editing a file with spaces (like hello world), or running a file with spaces in it (like tic tac toe)???

---

### Post by WorMzy on 2011-04-16
Escape the spaces, or use quotes.

e.g.

```
gedit hello\ world
gedit "hello world"
```

---

### Post by javajames97 on 2011-04-16
* sorry i understand gedit now :    gedit "hello world"

---

### Post by WorMzy on 2011-04-16
It's not just gedit. Most (if not all) applications need you to do that.

---

### Post by JRV on 2011-04-16
Please mark your thread solved.

---

### Post by javajames97 on 2011-04-16
but it's not solved, how to i START a app from terminal if it has spaces, i can usually start an app from it's name

---

### Post by pqwoerituytrueiwoq on 2011-04-16
if app name is "hello world"
type
hello\ world
it may be necessary to specify it's location
/usr/bin/gedit\ copy

---

### Post by WorMzy on 2011-04-16
I don't know of any applications with spaces in their names, but I would assume escaping (using "\"s) would work just as well in that case too.

---

