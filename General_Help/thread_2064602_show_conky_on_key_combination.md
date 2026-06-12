---
title: "show conky on key combination?"
date: 2012-09-29
forum: General Help
---

### Post by GreatDanton on 2012-09-29
I was wondering if it's possible to show conky, whenever I press some key combination (for example: alt+c). The conky would be hidden in the background and when I press key combination it will show up. If I would press the combination again the conky would disappear. 

Is this possible to make?

---

### Post by Toz on 2012-09-29
I'm not sure about the hidden in the background part, but you can create a script to kill conky and to restart it again depending on whether it is currently running, then make the script executable and assign it to the key combination Ctrl+C.

Something like this should work:
```

#!/bin/bash

#command to start conky - change to current conky startup command
CONKYCOMMAND="conky -d"

#check to see if conky is running
if [ "`ps -ef | grep conky | grep -v grep`" ]
then
        #if it is, then kill it
        pkill conky
else
        $if its not, start it up
        $CONKYCOMMAND &
fi
exit 0

```

Just replace the CONKYCOMMAND with the actual command that you use to start conky.

---

### Post by GreatDanton on 2012-09-30
Thank you Toz but the script is not working. With script I am able to close conky (with shortcut ctrl+alt+c), however I am not able to start it. If I run script in terminal this is the output:
```
Terminated
```Here is my current script:
```
#!/bin/bash

#command to start conky - change to current conky startup command
CONKYCOMMAND="conky"

#check to see if conky is running
if [ "`ps -ef | grep conky | grep -v grep`" ]
then
        #if it is, then kill it
        pkill conky
else
        #if its not, start it up
        $CONKYCOMMAND &
fi
exit 0
```Also I replaced $ with # in the line: if its not, start it up. I assume that line was meant as a comment.

Regards.

---

### Post by Toz on 2012-09-30
> **GreatDanton said:**
> Thank you Toz but the script is not working. With script I am able to close conky (with shortcut ctrl+alt+c), however I am not able to start it. If I run script in terminal this is the output:
```
Terminated
```Here is my current script:
```
#!/bin/bash

#command to start conky - change to current conky startup command
CONKYCOMMAND="conky"

#check to see if conky is running
if [ "`ps -ef | grep conky | grep -v grep`" ]
then
        #if it is, then kill it
        pkill conky
else
        #if its not, start it up
        $CONKYCOMMAND &
fi
exit 0
```Also I replaced $ with # in the line: if its not, start it up. I assume that line was meant as a comment.

Regards.
No, leave the $ as is - it references the variable earlier and executes it. How do you normally start conky? What command do you use? Make sure that command is in the quotes after the first reference to the variable CONKYCOMMAND and make sure that the last reference to CONKYCOMMAND is as:
```

$CONKYCOMMAND $
```

EDIT: And oh, you have to run the script twice for the toggle to work. If conky is running, the first time you execute the script, conky will close. The second time you run it (and/or if conky is not running), it will start up conky.

---

### Post by GreatDanton on 2012-09-30
I changed it like you suggested, but it's still not working.
This is the script: ```
#!/bin/bash

#command to start conky - change to current conky startup command
CONKYCOMMAND="conky"

#check to see if conky is running
if [ "`ps -ef | grep conky | grep -v grep`" ]
then
        #if it is, then kill it
        pkill conky
else
        $if its not, start it up
        $CONKYCOMMAND $
fi
exit 0
```To start conky I am using command: **conky**. > EDIT: And oh, you have to run the script twice for the toggle to work.  If conky is running, the first time you execute the script, conky will  close. The second time you run it (and/or if conky is not running), it  will start up conky.     If the conky is running I am able to close it (shortcut is working), however when I press shortcut/run script via terminal I am not able to start up conky.  The message in terminal is still the same. Are you able to see which part of the script is not working?

Thanks.

---

### Post by Toz on 2012-09-30
Oops, typo in the previous post. The 3rd last line should read:
```
$CONKYCOMMAND [COLOR="Red"]&[/COLOR]
```

When conky has been killed, can you post back the results of:
```
ps -ef | grep conky | grep -v grep
```

> To start conky I am using command: conky. 
Try setting the conky command to:
```
conky -d
```
... the -d for daemon mode.

---

### Post by Vaphell on 2012-09-30
simplified version of that script works here:
```
if pgrep conky; then pkill conky; else conky; fi
```
pgrep works like pkill (but doesn't kill anything, merely returns pids) and is tidier that ps | grep | grep -v

when i run that line in two terminals, first run launches conky, second one kills it

i think & is not really necessary - if conky gets killed, its launcher script will exit either way.

---

### Post by GreatDanton on 2012-09-30
Script:
```
#!/bin/bash

#command to start conky - change to current conky startup command
CONKYCOMMAND="conky -d"

#check to see if conky is running
if [ "`ps -ef | grep conky | grep -v grep`" ]
then
        #if it is, then kill it
        pkill conky
else
        $if its not, start it up
        $CONKYCOMMAND &
fi
exit 0
```ps -ef | grep conky | grep -v grep ===> After I close conky, the command returns nothing.

Output of terminal:```
Terminated

```

---

### Post by GreatDanton on 2012-09-30
@Vaphel I also tried your suggestion and it's not working either =).
output of the terminal:
```
31318
Terminated
```


Regards.

---

### Post by Vaphell on 2012-09-30
in my 10.04 i created custom hotkey under ctrl+f12
i typed
```
sh -c 'if pgrep conky; then pkill conky; else conky; fi'
```
in command field.

When i press the hotkey, conky shows up, when i press again it disappears, another press - shows up again, ...

---

### Post by Toz on 2012-09-30
@Vaphell's suggestion works for me as well. The code is tighter and cleaner than mine, but both work.

@GreatDanton, are you executing the command twice? Once to kill and once to re-start? When conky is killed, does the command "pgrep conky" return a process id (it shouldn't)?

---

### Post by GreatDanton on 2012-10-01
@Toz yes I am. When I kill conky, and then use the command you gave me before the command returns nothing.

@Vaphell
I misunderstood you. The command is working very well. I am currently using it, however the problem is not really solved, since I have future plans for this script.

Regards.

---

### Post by zombifier25 on 2012-10-01
If you use Compiz, then there's the Widget Layer plugin that will do what you want. If you're not using Compiz, then nevermind :P

---

### Post by GreatDanton on 2012-10-06
Sorry for the late answer, but yes I am using compiz.

---

