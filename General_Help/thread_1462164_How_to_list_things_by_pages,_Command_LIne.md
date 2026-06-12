---
title: "How to list things by pages, Command LIne"
date: 2010-04-25
forum: General Help
---

### Post by pepsifx357 on 2010-04-25
I know there has to be a flag of some kind that I can add to any entry I type that lists more than one page of information.  Like when I CD into a directory, then type ls to get the contents.  The information flows through pages then I only get to see the last page.  In the windows command prompt, a "/p" tag would make it to where I could scroll down the, rather large, list. What to I have to type to get that same feature in Ubuntu server?

---

### Post by sisco311 on 2010-04-25
Pipe it into less or more:

```
ls | less
```
```
ls -al | more
```

EDIT: See:
```
man bash | less +/Pipelines
``` ;)

---

### Post by pepsifx357 on 2010-04-25
Thank you very much!

---

### Post by oldos2er on 2010-04-25
Or you can use Shift-PageUp and Shift-PageDown to scroll through console output.

---

