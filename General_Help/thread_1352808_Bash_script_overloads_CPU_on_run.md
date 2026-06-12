---
title: "Bash script overloads CPU on run"
date: 2009-12-12
forum: General Help
---

### Post by mashiox on 2009-12-12
I've written two scripts one that starts the process if it hasn't been started already and the other that on start waits for the process to crash and then restarts it.
The one that causes problems is the latter.
It's form is close to exact to it's sister script, bit a little slimmer because I just didn't want this one to do as much.

On execution, this script causes the CPU to spike and hold at 100%.
Since the two scripts are very alike, I don't know where the problem is.
I've used the sleep, and echo "" > /dev/null, command to hold from sucking half my resources, but writing to /dev/null in a loop still sucks down the resources, and the script won't actually do anything if I use sleep.
I've thought about using the wait command, but I'm unsure of how to use it here.

Here's the script. 

```
#!/bin/bash
tcore=`pgrep AppName`
clown="email@domain.com"
cnt=0
subcnt=0

if [ -n $tcore ] 
then
	until [ -z "$tcore" ]
	do
		if [[ ! -x /home/trinity/trinitycore2/main/bin/trinity-core ]]
		then
			echo "AppName could not recover from a crash" | mail $clown
		elif [[ -x /path/to/application && -z "$tcore" ]]
		then
			echo "AppName recovered from a crash" | mail $clown
			/path/to/application
			let subcnt=0
		fi
			if [ $subcnt = 0 ] && [ -z "$tcore" ]
			then
				echo "AppName has crashed. Attempting to restart..." | mail $clown
				let subcnt=subcnt+1
			fi
	done
fi



```

---

### Post by efflandt on 2009-12-12
This is a little example of how to start a process in the background and wait for it to finish (or crash I think):

```
#!/bin/bash
coproc gedit
echo $COPROC_PID
wait $COPROC_PID
echo "All done!"
```Although, if you were actually running the script as a background process (scriptname &), you might want to redirect output of the coproc command and any other output to a log file.

```
#!/bin/bash
command=gedit
log=~/my.log

# insert code here to loop following
echo Start $command `date`>> $log
coproc $command 2>&1 >> $log
wait $COPROC_PID 2>&1 >> $log
echo Ended $command `date` >> $log
```

PS: The 2>&1 redirects std error (2) to std out (1) and that all gets appended (>>) to the log.

---

