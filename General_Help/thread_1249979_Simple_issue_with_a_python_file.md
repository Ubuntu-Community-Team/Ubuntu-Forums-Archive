---
title: "Simple issue with a python file"
date: 2009-08-26
forum: General Help
---

### Post by jerome1232 on 2009-08-26
Well I'm taking a python course at my community college, the professor wants us to use a template downloaded from his site for our programs.

I added a shebang at the beginning so I don't have to call python everytime I want to try and run the program.

For some reason there's an odd character in there though, when I try and run it I get this (offending character is in red):

```
bash: /home/jeremy/bin/assignment01.py: /usr/bin/python[COLOR="Red"]^M[/COLOR]: bad interpreter: No such file or directory
```

When I edit the file there is no whitespace or anything after the shebang so I'm really lost as to where this character is coming from....

The program works just fine when I call it with python.

---

### Post by jerome1232 on 2009-08-26
Okay I figured out the text file was created on his mac and I guess they have different new line symbols than linux, so I found a program in the repos tofrodos that can convert the new lines, it works after having run that program on it.

---

