---
title: "tail and awk execute command for each newline"
date: 2010-01-30
forum: General Help
---

### Post by SSzretter on 2010-01-30
I hope someone can help- 
I want to execute a command every time tail finds new lines in my text file.   I found something close, but it does not seem to work:

 tail -f screenlog.0 | awk '/\n/ {system("echo($1)")}'

I want it to echo the line every time there is a new line  (I will be doing something other than echo in the future)

thanks!

---

### Post by lloyd_b on 2010-01-31
> **SSzretter said:**
> I hope someone can help- 
I want to execute a command every time tail finds new lines in my text file.   I found something close, but it does not seem to work:

 tail -f screenlog.0 | awk '/\n/ {system("echo($1)")}'

I want it to echo the line every time there is a new line  (I will be doing something other than echo in the future)

thanks!

Searching for the newline is pretty much redundant, as Awk operates on line at a time basis anyway. So:```
tail -f screenlog.0 | awk "{ print }"
```will print every line.  You can then add search/comparison functions to the Awk command to limit which lines will print.

Lloyd B.

---

### Post by SSzretter on 2010-02-01
What if I wanted to output the line based on a carriage return?

---

### Post by lloyd_b on 2010-02-01
> **SSzretter said:**
> What if I wanted to output the line based on a carriage return?

If you want to search for lines with an actual <CR> (carriage return), then use "\r" in the search parameter.

Lloyd B.

---

