---
title: "bash: run multiple parallel threads"
date: 2011-07-06
forum: General Help
---

### Post by WDYSUN on 2011-07-06
Hello Dears

I have a script where I run a sequence of commands like this

```

#!/bin/bash

# Working directory 
WDIR="/home/user/dir"

command_1

command_2

command_3

command_4



```


Now this way the Bash will wait the end of command_1 before to start command_2. Since all this commands are independent from each other I would rather like to have them starting simultaneously before I have a quad core and each of these commands will use a single core.

There is any way to run independent  commands in parallel rather than in sequence?

Thanks in advance for your help

Best Wishes
Pietro

---

### Post by dethorpe on 2011-07-06
You could put each command into the background using the & operator, they'd be completly independent and run seperatly while the main script continued.  Probably not ok if you want more control of the threads, e.g. knowing when they all finish, but may do the job.
 
e.g:
 
command_1 &
 
command_2 &
 
etc

---

### Post by dethorpe on 2011-07-06
Continued .... 
 
Actualy can probably use "jobs" and/or "wait" commands in main script so it can wait at the end until all background jobs have finished if you want.

---

### Post by WDYSUN on 2011-07-06
That was not the actual scritp, it was just an example. I can do what you say  but I need something aouthomatic.

Best
Pietro 


> **dethorpe said:**
> You could put each command into the background using the & operator, they'd be completly independent and run seperatly while the main script continued.  Probably not ok if you want more control of the threads, e.g. knowing when they all finish, but may do the job.
 
e.g:
 
command_1 &
 
command_2 &
 
etc

---

### Post by Habitual on 2011-07-07
I just went through this but using yad. Show a progress meter while my function did it's thing (that took 11s to do).

I find help on [Unix.com/shell-programming-scripting](http://www.unix.com/shell-programming-scripting/). It is an invaluable resource. :wink:

---

