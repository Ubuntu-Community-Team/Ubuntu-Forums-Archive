---
title: "shell script advice needed"
date: 2010-03-09
forum: General Help
---

### Post by dln9 on 2010-03-09
I want to write a script that will do this when it is executed:  

Open an xterm terminal window
run the ls command on the current directory
show the results of the ls command
return the command prompt within the xterm terminal window so I can enter whatever other command I may feel like running next

I created this script:  

xterm -hold -e ls

It does everything I want, except it does NOT finish up by providing a command prompt.  Instead, I end up with a "dead" terminal window that does show the output of the ls command, but I can't then issue further commands within that same terminal window as I want to.  

Any ideas?  Thanks.

---

### Post by darolu on 2010-03-09
If I understood correctly you only need to do:
```
#!/bin/bash
xterm & ls
```

---

### Post by dln9 on 2010-03-09
Thank you.  

When I use your suggested script, all I get is the xterm terminal window with the command prompt.  The ls command - and its output - does not show at all.  It behaves just as if the script merely said this:  

xterm

instead of 

xterm & ls


Any other thoughts?

---

### Post by BenAshton24 on 2010-03-10
```
xterm -hold -e "ls && /bin/bash"
```
That should do it :)

---

### Post by dln9 on 2010-03-10
Ben Ashton, you did it!  It worked perfectly, thanks a lot.

---

### Post by dln9 on 2010-03-10
Wait - for some reason, the code that Ben Ashton provided on this forum is different from the code that appeared in the email from the forum notifying me that Ben Ashton had responded.  Very strange.  

Anyway - here is the correct code that works:  

xterm -hold -e /bin/bash -l -c "ls && /bin/bash"

---

### Post by BenAshton24 on 2010-03-10
> **dln9 said:**
> Wait - for some reason, the code that Ben Ashton provided on this forum is different from the code that appeared in the email from the forum notifying me that Ben Ashton had responded.  Very strange.  

Anyway - here is the correct code that works:  

xterm -hold -e /bin/bash -l -c "ls && /bin/bash"

It's because I edited it when I realized that you could achieve the exact same thing with a much shorter command. Both should work :)

---

