---
title: "executing commands in parallel + bash script"
date: 2011-01-29
forum: General Help
---

### Post by mahmoodn on 2011-01-29
I have a bash file which contain:
```
#!/bin/bash
./run1
./run2
./run3
```

Now when I run that script, they are executed serially in order. How can I assign or bind each one with a specific core. I mean they can be run in parallel.

---

### Post by gufide on 2011-01-29
are you talking about multi-threading in bash?

---

### Post by AlphaLexman on 2011-01-29
My first thought was the **nice** command, but a little research makes me think the **chrt** command is more in tune to your needs.

And, [Process Scheduling]("http://oreilly.com/catalog/linuxkernel/chapter/ch10.html")

---

### Post by cjhabs on 2011-01-29
> **mahmoodn said:**
> I have a bash file which contain:
```
#!/bin/bash
./run1
./run2
./run3
```Now when I run that script, they are executed serially in order. How can I assign or bind each one with a specific core. I mean they can be run in parallel.

The following should do it:

./run1&
./run2&
./run3&

The & puts the process in the background.

---

### Post by mahmoodn on 2011-01-30
> the chrt command is more in tune to your needs
Ho can I use it? which option is suitable?

> The & puts the process in the background
Yes, by putting each one in backgroung the others can be run in parallel. How about explicitly bing to a cpu?

---

### Post by cjhabs on 2011-01-30
> **mahmoodn said:**
> 
Yes, by putting each one in backgroung the others can be run in parallel. How about explicitly bing to a cpu?

I don't know, but I don't do heavy enough processing to worry about it - I let the OS manage it.

---

### Post by mcduck on 2011-01-30
> **cjhabs said:**
> I don't know, but I don't do heavy enough processing to worry about it - I let the OS manage it.

That would pretty much give the best result in the end, heavy processing or not. The kernel's scheduler probably does better job than most people would be able to do anyway, as it knows what all the other processes running on the system are and what core they are using.. ;)

However, if you still want to bind a process to a specific core, [http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html]("http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html").

---

### Post by AlphaLexman on 2011-01-30
> **mahmoodn said:**
> How can I use it? which option is suitable?
You have to make those decisions, what [commands | programs] are you trying to execute at the _*same*_ time? What priorities do they need? How much processor power do they require? How much disk usage do they need?

With '**chrt**' you can define all of these priorities.

---

### Post by Ole Tange on 2011-03-18
You might want to take a look at GNU Parallel.

[http://www.youtube.com/watch?v=OpaiGYxkSuQ](http://www.youtube.com/watch?v=OpaiGYxkSuQ)

---

