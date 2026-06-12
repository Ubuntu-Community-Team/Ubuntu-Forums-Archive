---
title: "open new terminal prompt"
date: 2009-07-13
forum: General Help
---

### Post by tomdagreek on 2009-07-13
had a question..
im running 8.04 lts server with terminal and have not gone the way of adding a desktop gui.
when i run a binary it comes up and starts to run.
is  there a way of bring the terminal prompt back so i can run another bin?
i have googled starting a new terminal and it seems to me that most responses were for folks with some kind of gui installed

i am getting better with running the terminal commands but am still a noobie boobie

tom

---

### Post by starcraft.man on 2009-07-13
Easy solution for you friend, you want to learn to run commands in the background. Basically, if you put the & at the end of a command like (assuming large data move) :

```
cp /path /destination &
```

It will run in the background and notify you when it's done. There is nuance to this, you want to look up the *jobs* and *fg* commands as well. You'll need them to keep track of things if you start running lots of commands. I don't have a tut off hand, I learned about them via a book (not free). Google should find ya something quick though.

---

### Post by dfreer on 2009-07-13
There is also the multiple virtual terminals (Ctrl + Alt + F1-6), you can run a command in one then switch to another. Anothe great command is screen, I use this on my server to quickly check running game servers and check memory usage.

---

### Post by t4thfavor on 2009-07-13
suprised nobody mentioned screen..


screen ./executable

then ctrl+ad to detach

then screen -x to reconnect. if you have lots of them running it will ask which one and you must specify PID.

easy.

---

### Post by tomdagreek on 2009-07-13
thanks u guys...
in my defense i have ordered a couple of books off amazon but they have not arrived yet..
the terminal is not for the timid.. I am willing to bet that i have asked google more questions than i have of my parents- but i have realized that while ubuntu desktop is very slick it is running alot of processes that i am not using..

---

