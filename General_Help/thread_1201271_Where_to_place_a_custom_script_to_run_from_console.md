---
title: "Where to place a custom script to run from console"
date: 2009-06-30
forum: General Help
---

### Post by pythonscript on 2009-06-30
Where in the file hierarchy should I put a script I want to access from the terminal at all times? In this case, it's a shell script, so should I just place *myscript.sh* in the /usr/bin directory? Will this work for all users? If this was *myscript.py* instead, would the same procedure still apply? Sorry about the numerous questions. Thanks!

---

### Post by t4thfavor on 2009-06-30
Yes, that is where I would put it. It will work for all users if you give it all execute permissions. I also belieeve that a py script will work the same. Just be sure to include the #!/usr/bin/python or #!/bin/bash line so that the shell knows what to do with it.

---

### Post by pythonscript on 2009-07-02
Thanks! Exactly what I was looking for.

---

