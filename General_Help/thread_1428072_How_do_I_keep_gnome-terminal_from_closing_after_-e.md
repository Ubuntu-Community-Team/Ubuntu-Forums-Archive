---
title: "How do I keep gnome-terminal from closing after -e?"
date: 2010-03-12
forum: General Help
---

### Post by MikeJRamsey on 2010-03-12
From a bash script, I want to 
1. Open a gnome-terminal
2. Give it a title
3. cd to a directory
4. Execute an initial command
5. Stay open

So I try this
#!/bin/bash
gnome-terminal -t Terminal --working-directory ~/tasks -e date

There is a flash, and the window disapers.

How do I get the window to stay open?

Thank you.

---

### Post by kaibob on 2010-03-12
The following command will do what you want:

```
gnome-terminal --title=TestTitle --execute bash -c "cd /home/kaibob ; date ; bash"
```

You can use read instead of bash at the end if you do not want a command prompt after the command has run. In that instance, you press the enter key to close the terminal.

---

