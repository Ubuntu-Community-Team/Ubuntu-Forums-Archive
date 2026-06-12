---
title: "regexp r-search in bash"
date: 2010-07-13
forum: General Help
---

### Post by Zorgoth on 2010-07-13
What keyboard shortcut will give me a regexp reverse search in bash?  Or does C-r supply something like that already that I can't figure out?

---

### Post by prodigy_ on 2010-07-13
Hmm?

If you want to reverse a string, the command you need is **rev**. If you want to reverse the order of lines in a file, the command is **tac**. Both these commands combined effectively reverse everything (i.e. the last symbol of the file becomes the first in the output and vice versa).

---

### Post by Zorgoth on 2010-07-13
Sorry, maybe I haven't made myself clear.  I do not want to reverse a string.  I want to search through past bash commands with a regular expression.  You can search through past bash commands using the keyboard shortcut C-r, but that does not, as far as I can tell, support regexps.

---

### Post by prodigy_ on 2010-07-13
Don't know about keyboard shortcuts but the command would be: ```
grep '<your_regular_expression>' ~/.bash_history
```

Hope that helps.

---

### Post by Zorgoth on 2010-07-13
Thanks.  I know you can do that with a command though.  I am looking for a keyboard shortcut.  I titled and wrote this thread very badly; I wish I could change the title...

---

