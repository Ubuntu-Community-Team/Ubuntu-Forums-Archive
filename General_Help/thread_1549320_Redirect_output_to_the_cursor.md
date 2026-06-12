---
title: "Redirect output to the cursor?"
date: 2010-08-09
forum: General Help
---

### Post by lariosa42 on 2010-08-09
Hello,

I would like to be able to do something like this:
```
sleep 2 && echo $PWD >$?
```

where "?"  is some way of outputting to the text cursor. During [FONT="Courier New"]"sleep[/FONT]," the idea is that I place my cursor in, say, a text box.  Then when "[FONT="Courier New"]sleep[/FONT]" is completed, I want my text box to fill up with the output of "[FONT="Courier New"]echo $PWD[/FONT]."  Does anybody know how to do this?  I don't care if it's done with a "[FONT="Courier New"]>[/FONT]" redirection or something else.

By the way, my ultimate goal is to bind "[FONT="Courier New"]date +%Y%m%d[/FONT]" to a key combination, so I can easily output YYYYMMDD to filenames, etc.

Thanks in advance!

---

