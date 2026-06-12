---
title: "Is there some way a script can tell if a program is running?"
date: 2011-01-14
forum: General Help
---

### Post by canam101 on 2011-01-14
Is there a file that can be opened and a program name searched for? If it is there, the program is running, else it is not.

Something like that?

I have a program that stops periodically. If I could run a script every 30 minutes or so to check the hypothetical file, it could re-start the program if the program had stopped running.

---

### Post by TeoBigusGeekus on 2011-01-14
```
#!/bin/bash
if ps ax | grep program_terminal_name > /dev/null
then
    echo "Move along, nothing to see here..."
else
    commandtolaunchprogram
fi
```

---

