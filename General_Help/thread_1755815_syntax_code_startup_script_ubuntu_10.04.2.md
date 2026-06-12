---
title: "syntax code startup script ubuntu 10.04.2"
date: 2011-05-11
forum: General Help
---

### Post by remymf on 2011-05-11
):P I am trying to write a script that executes at startup, i have tested it and it kind of works. Now i would like to make it check to see if it is still running. my old script was
 
#!/bin/sh
tsclient -x startup.rdp
 
it opened a remote connection to the computer i wanted, however sometimes it will switch back to my ubuntu desktop. Any ideas on why it does this? in short i want to make a script that runs forever basically and looks like this. If you can help with syntax, i would greatly appreciate it
 
#!/bin/bash
 
Function = checkit
 
if
tsclient "is running" startup.rdp
show that window
wait 10s
run checkit
else
tsclient -x startup.rdp
wait 10s
run checkit
fi
 
How do i accomplish this?:confused:

---

