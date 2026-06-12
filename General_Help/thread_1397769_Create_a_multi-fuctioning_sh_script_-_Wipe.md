---
title: "Create a multi-fuctioning sh script? - Wipe"
date: 2010-02-03
forum: General Help
---

### Post by WubWubi on 2010-02-03
I have several commands I would like to run with the software called Wipe. I have several locations I would want wiped and want to make an sh script to run Wipe and delete the locations. However I would like to have Terminal left open so I can see what it's wiping and once it's finished move on to the next location, is this possible and how would I do it?

The locations are:

/tmp
Firefox cache
flash cache
recently-used (file)

Not sure if there are any more locations and log files that could be entered, Ccleaner used to do all these things for me, the DIY part of Linux is quite fun though, :D

---

### Post by bodhi.zazen on 2010-02-03
Sounds as if you want to run a bash script =)

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

[http://www.panix.com/~elflord/unix/bash-tute.html]("http://www.panix.com/%7Eelflord/unix/bash-tute.html")

Basically

```
#!/bin/bash

command 1
command 2

exit 0
```Save that as say ~/bin/clean

chmod a+x ~/bin/clean

Call the script as sudo.

As an alternate you may wish to look at "computer janitor" or bleachbit.

---

### Post by WubWubi on 2010-02-03
Thanks for the information, before I go on to read those links, how do I keep the terminal window open after everything has finished so I can close it myself?

---

### Post by bodhi.zazen on 2010-02-03
Open a terminal and manually run the script.

---

