---
title: "Question Regarding Easy Linux command"
date: 2012-08-23
forum: General Help
---

### Post by Alcidious on 2012-08-23
So I'm working on a little project.  I like writing to-do lists in plain text editors, labeled as Today.txt and so on.  I want to be able to create an updated "Current_ToDo" through (in a terminal).  This is my first step:

cat 8_16 8_17 > CurrentTodo

So, suppose there's another list, 8_15 , which has some of the same tasks as 8_16 and 8_17 (unfinished tasks that go into CurentToDo), but also there is some other task that was not completed. How do I search for this string? What terminal command can search for that third string (the other task, let us say z), distinguish it from the other two tasks also in 8_16 and 8_17 (say tasks x y ).

Could I use: grep x y 
-and get something displaying 8_15 and z?

Thanks! Trying!

---

### Post by codemaniac on 2012-08-23
You might look at the -f switch of grep , which reads one or more patterns from the  file .Please refer to manual page of grep .

---

### Post by 2F4U on 2012-08-23
I honestly don't want you to keep writing your own tools, but if you want a serious tool for todo lists and outlines and much more, then look at Org-mode:

[http://orgmode.org/](http://orgmode.org/)

---

### Post by Alcidious on 2012-08-23
I appreciate the input! To be honest, I'd had a couple glasses of wine before playing with my computer.  Really I'm just trying to become a more advanced user and programmer, but while I've been reading quite a bit I was hoping folks with more experience could point out some useful commands for me to look into.

---

### Post by codemaniac on 2012-08-24
Linux shell offers you an array of advanced text processing tools that can do any type of text processing job on hand .You can have a look at the filters grep , sed , cut , head , tail , uniq , sort , cat and many other .

[http://en.wikipedia.org/wiki/Filter_(Unix](http://en.wikipedia.org/wiki/Filter_(Unix))

---

