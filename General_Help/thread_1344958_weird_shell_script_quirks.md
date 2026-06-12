---
title: "weird shell script quirks"
date: 2009-12-03
forum: General Help
---

### Post by treehouse on 2009-12-03
I use a shell script at startup to make my neato desktop terminal. It wasn't working due to the sleep command not working. I tried to figure it out by adding echo lines to debug it, and it automagically worked, when I comment them out, it doesn't work. It's not really a problem as I don't run this script in a terminal, but I was wondering if anyone knew why it's acting like this?

```


#!/bin/bash
# sleep to prevent interference with gnome-panel and whatever else

echo "sleep 20"
sleep 20 && 
echo "end sleep 20"

echo "start devilspie"
devilspie &
PID_DEVILSPIE=$!
echo "end devilspie"

# start the terminal
echo "start gnome-terminal"
gnome-terminal --geometry=162x62+5+28 --window-with-profile=DesktopConsole &
echo "end gnome-terminal"

echo "second sleep"
sleep 10 &&

# kill devilspie since I don't use it for anything else but this
echo "kill devilspie"
kill -9 $PID_DEVILSPIE
echo "done"

```

:P

---

### Post by Brandon Williams on 2009-12-03
The problem is the trailing "&&" at the end of your sleep command, which is a logical AND. It will concatenate the sleep command and the next command into a single command line, executing the second command after sleep completes.

If the list of commands looks like this:
```
sleep 10 &&
develspie &
```
then the command line 'sleep 10 && develspie' will be executed in the background while the rest of the script continues to run, since the final '&' applies to the entire command line.

If the command list looks like this:
```
sleep 10 &&
echo "end sleep 10"
```
Then the command line 'sleep 10 && echo "end sleep 10"' will be executed, and since it is not backgrounded, no other commands in the script will be executed until this command line is complete.

From the look of the script, you want to remove the "&&" from the ends of all the lines that execute sleep.

---

### Post by treehouse on 2009-12-04
Thanks, I read about the '&&' somewhere else and it didn't tell me it concatenates.

---

### Post by falconindy on 2009-12-04
Actually, it doesn't concatenate. It really does work as a logical 'and' operator. I use this all the time in scripting to replace if/then structures. Suppose the following:

```
./prog1 && ./prog2
```

If prog1 exits with an error, the statement absolutely must be false. The shell will not continue with that line, and prog2 will never be executed. It's only when prog1 exits successfully that prog2 will run.

Similarly, you can use the || (logical 'or'):

```
./prog1 || ./prog2
```

If prog1 exits with success, the statement absolutely must be true. The shell will not continue evaluating the statement and prog2 will not run. However, prog2 **will** run if prog1 exits with an error. This in particular is used very often in build scripts to exit immediately if one part of the build fails.

---

