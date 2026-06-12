---
title: "is there an echo in here?"
date: 2012-01-16
forum: General Help
---

### Post by conradin on 2012-01-16
Some times I want to append a file with multiple lines via echo. 
Im reading the man page for echo and see the \n option, but I cant get the syntax to give me what I want. 
```
echo "#" Some User Defined Aliases \n GREP_OPTIONS='grep --color=always' > ~/ngo
```

that gives me one line at the end of a file where I want 2 lines.

---

### Post by jim_deadlock on 2012-01-16
You need the -e flag, try this:

```
echo -e "# Some User Defined Aliases\nGREP_OPTIONS='grep --color=always'" > ~/ngo
```

---

### Post by papibe on 2012-01-16
In order for the '\n' to work you need to use the -e option. Also you need to put all between quotes:
```
echo -e "# Some User Defined Aliases \nGREP_OPTIONS='grep --color=always'" >> ~/ngo
```
Note the use of '>>' instead of just '>' (so you append the lines instead of overwritten the file).

Hope it helps.
Regards.

---

### Post by conradin on 2012-01-17
Thanks Jim! Thanks papibe!
I got it now!
:guitar:

---

