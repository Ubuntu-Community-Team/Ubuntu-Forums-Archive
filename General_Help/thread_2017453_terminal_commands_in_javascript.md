---
title: "terminal commands in javascript"
date: 2012-07-05
forum: General Help
---

### Post by netopalis45 on 2012-07-05
I have a javascript page that I would like to use to run terminal commands and possibly show the output from those commands on that page. Google was very unhelpful as I don't think it could understand what I wanted. Specifically I would like to use the cat command to read a file, I can do this in a .sh file with $(cat /home/file) and I would like to do something similar except with javascript on my page. Ideas?

---

### Post by msammels on 2012-07-05
I'm not sure if this is possible. You can, if you so wish, do it with PHP, but you cannot execute system commands from Javascript.

Even if you could, I wouldn't recommend it, as its terribly unsafe, and opens up your system, creating a massive security hole :P

---

### Post by netopalis45 on 2012-07-05
The page is password protected so I don't believe it would be a security problem

---

### Post by netopalis45 on 2012-07-05
How about just reading the contents of a .txt file into one of the javascript commands? I think I could figure it out from there. (Again it would be similar to using $(cat /home/file.txt) to pass the contents of that file to a variable in a .sh script)

---

### Post by dcstar on 2012-07-06
> **msammels said:**
> I'm not sure if this is possible. You can, if you so wish, do it with PHP, but you cannot execute system commands from Javascript.

Even if you could, I wouldn't recommend it, as its terribly unsafe, and opens up your system, creating a massive security hole :P

100% correct, Javascript is a set of limited capability commands that specifically do not spawn off into commands that could do whoever knows what.

If you want stupid capabilities that could possibly wreck systems then I suggest people look at the various Microsoft products.

---

