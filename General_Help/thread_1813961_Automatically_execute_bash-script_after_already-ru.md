---
title: "Automatically execute bash-script after already-running process finishes?"
date: 2011-07-28
forum: General Help
---

### Post by chellrose on 2011-07-28
I have a computation going which takes a long, but uncertain, amount of time.  I have another computation which needs to be run, but _after_ the first one is done.  I won't be at the computer at that time to manually start the new process.

I've done some Googling, and I found how to delay execution by a specific amount of time (e.g. "start process x in exactly 8 minutes from now), but that isn't quite what I want to do.  Essentially, I'd like to tell the shell, "When process #nnnn finishes running, then start process x".  Is there a way to do this?

Thanks.

---

### Post by lkjoel on 2011-07-28
> **Sissy13 said:**
> I have a computation going which takes a long, but uncertain, amount of time.  I have another computation which needs to be run, but _after_ the first one is done.  I won't be at the computer at that time to manually start the new process.

I've done some Googling, and I found how to delay execution by a specific amount of time (e.g. "start process x in exactly 8 minutes from now), but that isn't quite what I want to do.  Essentially, I'd like to tell the shell, "When process #nnnn finishes running, then start process x".  Is there a way to do this?

Thanks.
This is some code to find if process id nnnn is still running:
```
ps -ef | awk '{print $2}' | grep "^*PROCESSID*$"
```So to continually find if it is still running, try this:
```
export newcalc=0
while [ $newcalc -eq 0 ]
do
ps -ef | awk '{print $2}' | grep "^*PROCESSID*$" > /dev/null 2>&1
if [ $? -eq 0 ]
then
:
else
newcalc=1
fi
sleep .1
done
*yourcalculationhere*
```

---

### Post by lmarmisa on 2011-07-28
I recommend to create a bash script. The bash script file will contain all the commands that you want to execute. A command will no be started until the previous one is completed.

```

gedit yourscript.sh

``` 
This is an example of the contents:
```

#!/bin/bash
computation1
computation2

```

I recommend to add the execution privilege to your bash script:
```

chmod +x yourscript.sh

```

Finally you can run your bash script in several ways:

```

bash yourscript.sh
./yourscript.sh

```

---

### Post by lkjoel on 2011-07-28
> **lmarmisa said:**
> I recommend to create a bash script. The bash script file will contain all the commands that you want to execute. A command will no be started until the previous one is not completed.

```

gedit yourscript.sh

```This is an example of the contents:
```

#!/bin/bash
computation1
computation2

```I recommend to add the execution privilege to your bash script:
```

chmod +x yourscript.sh

```Finally you can run your bash script in several ways:

```

bash yourscript.sh
./yourscript.sh

```
Right, I forgot that you can to it the simple way lol!

---

### Post by chellrose on 2011-07-28
Thank you both.  The bash script would be nice, but unfortunately computation1 has already been running for quite some time.  I don't want to restart it, and it's not yet at the stage where it could easily pick up where it left off.  

@lkjoel: I'll try that routine.  Does the continual "find if it is running" process eat up a significant amount of CPU resources?

Thanks again.

---

### Post by lkjoel on 2011-07-28
> **Sissy13 said:**
> Thank you both.  The bash script would be nice, but unfortunately computation1 has already been running for quite some time.  I don't want to restart it, and it's not yet at the stage where it could easily pick up where it left off.  

@lkjoel: I'll try that routine.  Does the continual "find if it is running" process eat up a significant amount of CPU resources?

Thanks again.
It doesn't take too much CPU, since it only runs every .1 seconds.

---

### Post by Hemmer on 2011-08-04
For future reference, bash can handle this sort of thing:

> If you want to run each program, regardless if the preceding ones fail, separate them with semicolons:

 ```
 $ long ; medium ; short
```

If you only want to run the next program if the preceding program worked, and all the programs correctly set exit codes, separate them with double-ampersands:

  ```
$ long && medium && short
```

[[Source]]("http://www.devshed.com/c/a/BrainDump/Executing-Commands-with-bash/2/")

---

