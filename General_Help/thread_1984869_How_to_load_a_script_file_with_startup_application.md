---
title: "How to load a script file with startup applications"
date: 2012-05-22
forum: General Help
---

### Post by williammanda on 2012-05-22
I have tried to use the startup applications to start a script file on startup. I basically entered:
/home/name/scriptfile.sh
for the path and file but this doesn't work. Any simple ideas on how to get this to work with startup applications?
Thanks

---

### Post by roelforg on 2012-05-22
You need to chmod it +x (so you can execute it, i assume you already did this).
 
And you need a shebang line.
A shebang line tells what program should be used to run the script, it has to be on the first line of the script if you want the script to work outside the terminal.
A typical shebang line for a bash (shell) script is:
```

#!/bin/bash

```
PHP:
```

#!/usr/bin/php5

```
PERL:
```

#!/usr/bin/perl

```
Python:
```

#!/usr/bin/python

```

---

### Post by williammanda on 2012-05-22
Here is the script...adding the line you referred to is above my pay grade.

#!/bin/sh

java -Djava.net.preferIPv4Stack=true -jar BubbleUPnPServer.jar $*

---

### Post by roelforg on 2012-05-22
> **williammanda said:**
> Here is the script...adding the line you referred to is above my pay grade.
 
#!/bin/sh
 
java -Djava.net.preferIPv4Stack=true -jar BubbleUPnPServer.jar $*
 
Would you please use code tags?
 
But i see the line is already there... but i see some bash-specific and location specific code in there so try this version:
```

#!/bin/bash
java -Djava.net.preferIPv4Stack=true -jar /home/name/BubbleUPnPServer.jar $*

```
Save it and see if it runs in the terminal, if it does then you log out and back in and see if it worked!

---

### Post by williammanda on 2012-05-22
Your change works in terminal (./file.sh) 
but it isn't working with startup applications.

---

### Post by roelforg on 2012-05-22
> **williammanda said:**
> Your change works in terminal but it isn't working with startup applications.

I'll give you a screenshot of how it should look in your "Startup Applications".
(ignore the colors, that's just my theme)

---

### Post by williammanda on 2012-05-22
To clarify...I used ./script.sh in terminal and it worked....I tried script.sh and it didn't work. Sorry for the confusion but this is new to me.

---

### Post by roelforg on 2012-05-22
> **williammanda said:**
> To clarify...I used ./script.sh in terminal and it worked....I tried script.sh and it didn't work. Sorry for the confusion but this is new to me.

Try this version, you made me realize something:
```

#!/bin/bash
cd /home/name
java -Djava.net.preferIPv4Stack=true -jar /home/name/BubbleUPnPServer.jar $*

```
I think your prog wants some files in the current dir so we need to cd to the dir first.
This one should work.

Also, calling script.sh won't work because it'll cause bash to search its path var (it only contains the sys dirs, this is perfect for normal use), you need to give it a full path to the file (./script.sh is a full path, so is /home/name/script.sh or ~/script.sh).
It's normal that ./script.sh works and script.sh not, it's by design.

---

### Post by williammanda on 2012-05-22
> **roelforg said:**
> Try this version, you made me realize something:
```

#!/bin/bash
cd /home/name
java -Djava.net.preferIPv4Stack=true -jar /home/name/BubbleUPnPServer.jar $*

```
I think your prog wants some files in the current dir so we need to cd to the dir first.
This one should work.

Also, calling script.sh won't work because it'll cause bash to search its path var (it only contains the sys dirs, this is perfect for normal use), you need to give it a full path to the file (./script.sh is a full path, so is /home/name/script.sh or ~/script.sh).
It's normal that ./script.sh works and script.sh not, it's by design.

I did give the full path for the script file...just not in the last remark.

Lets back up a minute....the script file works. Right now I type in terminal /home/name/script.sh and it works just fine. All I want to do is automate it via startup applications. Now with that said...if what you are doing is aiding in the automation...great! If not then we are done. 
Thanks

---

### Post by roelforg on 2012-05-22
> **williammanda said:**
> I did give the full path for the script file...just not in the last remark.

Lets back up a minute....the script file works. Right now I type in terminal /home/name/script.sh and it works just fine. All I want to do is automate it via startup applications. Now with that said...if what you are doing is aiding in the automation...great! If not then we are done. 
Thanks

Your script relied on the current directory being your home dir,
with these automated scripts you can't rely on starting/being in a certain working dir, you need to go there yourself and also start the script with only the full path, this'll prevent nasty problems down the line.

So yes, i've been trying to make your script work for you.

I've made it my habit of starting my bash scripts like this:
```

#!/bin/bash
cd /full/path/to/expected/working/dir

```or a similar version for other scripting languages.

The screenshot i added demonstrates how i did it for the python script that binds xscreensaver to the "lock screen" command.

---

### Post by williammanda on 2012-05-22
Once I make the changes to the script file....am I suppose to use the "./" or not in terminal for a test?

---

### Post by roelforg on 2012-05-22
> **williammanda said:**
> Once I make the changes to the script file....am I suppose to use the "./" or not in terminal for a test?

Shouldn't matter, that's the whole point to making the changes:
It shouldn't/doesn't matter if you use the ./ /home/name or ~/ notation (it does matter though in the startup applications dialog) or what directory you're in!

---

### Post by williammanda on 2012-05-22
Adding the path and changing the sh to bash in the script file didn't work. What I mean by that is...typing script.sh in terminal just like when I typed ./script.sh (which ./script.sh works).

---

