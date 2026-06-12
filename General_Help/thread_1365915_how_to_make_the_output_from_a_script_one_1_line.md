---
title: "how to make the output from a script one 1 line"
date: 2009-12-27
forum: General Help
---

### Post by markp1989 on 2009-12-27
i have a script that  that outputs text  on multiple lines like this:

line 1
line 2
line 3
line 4

 i want to have the output go to one line with a colon between the lines like this : 

line 1 : line 2 : line 3 : line 4 : 

thanks Markp1989

---

### Post by dagarwal82 on 2009-12-27
> **markp1989 said:**
> i have a script that  that outputs text  on multiple lines like this:

line 1
line 2
line 3
line 4

 i want to have the output go to one line with a colon between the lines like this : 

line 1 : line 2 : line 3 : line 4 : 

thanks Markp1989
Have them appended in a string and echo. is this something you were looking for?

---

### Post by sisco311 on 2009-12-27
```
cat file | tr '\n' ':'
```

---

### Post by falconindy on 2009-12-27
'echo -n' or 'printf' won't provide a line break at the end of each line.

---

### Post by markp1989 on 2009-12-27
> **sisco311 said:**
> ```
cat file | tr '\n' ':'
```

that did what i wanted , thanks :D now my script works with dzen2 aswell as conky :D 

thanks Markp1989

---

