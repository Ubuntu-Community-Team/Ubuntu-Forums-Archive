---
title: "Terminal line overflows"
date: 2010-10-08
forum: General Help
---

### Post by l3ecl on 2010-10-08
When I type something really long, the terminal does not create a new line to accommodate the string. Instead, it overruns the same line. [IMG]http://img259.imageshack.us/img259/596/screenshotnq.png[/IMG]

---

### Post by sikander3786 on 2010-10-08
Might be because straight after hitting 'Enter', you again press down the 'a' key. Let the terminal finish a job and then give it the next command. It might happen not only with long syntax but also with short one. Try it yourself.

Nothing wrong for me at least.

---

### Post by Spice Weasel on 2010-10-08
This happened to me when I edited my ~/.bashrc. Try replacing the PS1 line in the file ~/.bashrc with this:

> 
PS1="\[\033[1;34m\](\[\033[1;37m\]\w\[\033[1;34m\]) \[\033[1;32m\]*\[\033[1;0m\] "


Use whatever text editor you like.

---

### Post by l3ecl on 2010-10-09
Thanks for the input. It definitely solved my problem but I don't understand how.

This is my old PS1 ```
 PS1="\e[1;33m[\u@\h:\W]$ \e[m"

```

I'm trying to understand the main difference between yours and mine but it's really confusing.

---

