---
title: "/bin/sh: bad interpreter"
date: 2011-03-22
forum: General Help
---

### Post by Don Barnett on 2011-03-22
When running ./configure to compile expect I get the error "/bin/sh: bad interpreter: No such file or directory."  I had this same problem when installing ActiveTc1 but solved it by going to an earlier version of ActiveTc1.  That didn't work with expect.
I am on version 8.04 and the /bin/sh is a link to dash.

Any Ideas?

Thanks
Don B

---

### Post by antaios256 on 2011-03-22
change the first line of the script 

the very top line of a script (a well written one anyways) will have a direct path to the interpreters 

#!/bin/sh - tells the script to run in the bourne shell, depending on which linux your using you might need to change that to 

#!/bin/bash

to run in the bash shell as the bourne shell is outdated and might not be be available in your distribution

---

### Post by raw937 on 2011-04-07
Hello,

I ran this command
for this other program SOrt-ITEMS


sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh

NOW, I am having all types of problems

Get this error for firefox:
Failed to execute child process "firefox" (No such file or directory)

Get this error for openoffice:
Failed to execute child process "ooffice" (No such file or directory)

And this in command line:
bash: /usr/bin/lesspipe: /bin/sh: bad interpreter: No such file or directory


WTF, which program is next!!!!!!!!!!!!!!!

---

