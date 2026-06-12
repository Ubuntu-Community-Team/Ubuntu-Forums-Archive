---
title: "Bash questions"
date: 2011-09-16
forum: General Help
---

### Post by layr on 2011-09-16
**1.** How to create loop within a script file? For instance creating a finite loop, which limit is defined by other arguments than running count?

Eg. script that checks whether a process is running; if it is, sleeps for say 5 sec, then checks again etc, until the program isn't running and completes the task.

Couldn't find a command as 'goto line' or such.

**2.** Is there a way to execute a command without printing any terminal output?

---

### Post by sisco311 on 2011-09-16
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Loops_.28while.2C_until_and_for.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Loops_.28while.2C_until_and_for.29)
and
[http://mywiki.wooledge.org/BashGuide/InputAndOutput](http://mywiki.wooledge.org/BashGuide/InputAndOutput)

```
while pgrep process-name > /dev/null 2>&1
do
    sleep 5
done

command
```

and

```
command > /dev/null 2>&1
```

---

### Post by layr on 2011-09-16
Thank you. I was already familiar with the while and until; actually a infinite loop was what i was looking for. Got it nailed this time.

Btw, what does that '2>&1' do after '/dev/null'?

---

### Post by ofnuts on 2011-09-16
> **layr said:**
> Thank you. I was already familiar with the while and until; actually a infinite loop was what i was looking for. Got it nailed this time.

Btw, what does that '2>&1' do after '/dev/null'?
Send standard error (handle #2)  to the same place as standard output (handle #1)

---

### Post by sisco311 on 2011-09-16
Well, in short **> /dev/null 2>&1** redirects both stdout and stderr to /dev/null.

Bash has a shorter version: *command **&>** file*, which does the same. It's handy in the interactive shell, but it's not portable, so it's not recommended practice. 

For detailed explanation check out the *File Redirection* & *File Descriptor Manipulation* sections from the second link in my previous post.

---

### Post by layr on 2011-09-17
> **sisco311 said:**
> Well, in short **> /dev/null 2>&1** redirects both stdout and stderr to /dev/null.

Bash has a shorter version: *command **&>** file*, which does the same. It's handy in the interactive shell, but it's not portable, so it's not recommended practice. 

For detailed explanation check out the *File Redirection* & *File Descriptor Manipulation* sections from the second link in my previous post.

Well, being novice with bash, it probably takes time to understand correctly.

Anyway, got the script done. It checks Banshee's status; if it's playing, creates file 'banshee_playing' and checks whether screenlet called impulse is running (and starts it, if not).

If banshee status isn't playing, script checks whether 'banshee_playing' exists; if it does, deletes it; also checks whether Impulse is running (kills it if is).

It runs fine. But when i log out from my account and log back in, it somehow starts creating and deleting 'banshee_playing' and starting/killing Impulse regurarly. What's with logging out?

```
#!/bin/bash
# Script starts and kills Impulse screenlet, as Banshee is playing or paused accordingly.
# Also creates file 'banshee_playing' to /tmp (for conky usage only)
## Prerequisites (required):
# conkyBanshee
# Banshee 
# Screenlets (and also Impulse -> http://screenlets.org/index.php/Impulse)
sleep 35
while :
do
status=`conkyBanshee --datatype=ST`
if [ $status = Playing ]; then
  	touch /tmp/banshee_playing &
	if ! pgrep -f ImpulseScreenlet.py; then
    		python -u /home/laur/.screenlets/Impulse/ImpulseScreenlet.py
	fi
    else
	if [ -f /tmp/banshee_playing ]; then
	rm /tmp/banshee_playing &
	if pgrep -f ImpulseScreenlet.py; then
	pkill -9 -f ImpulseScreenlet.py
	fi
	fi
fi &
sleep 5
done
```

---

### Post by sisco311 on 2011-09-19
I think it's because you run the if statement in the background. Remove the & from the end of **fi &**.

`command` is not POSIX, the POSIX form $(command) is recommended.

For comparing strings us [[ instead of [

```
#!/bin/bash
# Script starts and kills Impulse screenlet, as Banshee is playing or paused accordingly.
# Also creates file 'banshee_playing' to /tmp (for conky usage only)
## Prerequisites (required):
# conkyBanshee
# Banshee 
# Screenlets (and also Impulse -> http://screenlets.org/index.php/Impulse)

sleep 35
while :
do
    status=$(conkyBanshee --datatype=ST)
    if [[ $status == Playing ]]
    then
        > /tmp/banshee_playing 
        if ! pgrep -f ImpulseScreenlet.py
        then
            python -u /home/laur/.screenlets/Impulse/ImpulseScreenlet.py
        fi
    else
        # no need for the extra if statements
        # neither rm nor pkill won't complain if the file or process doesn't exist
        rm -f /tmp/banshee_playing
        # not sure here, but I'd probably try to term the process first
        pkill -15 -f ImpulseScreenlet.py || pkill -9 -f ImpulseScreenlet.py
    fi 
    sleep 5
done
```

---

### Post by layr on 2011-09-30
> **sisco311 said:**
> I think it's because you run the if statement in the background. Remove the & from the end of **fi &**.

`command` is not POSIX, the POSIX form $(command) is recommended.

For comparing strings us [[ instead of [
Sorry for delaying with reply.
I tested your version, also tried removing &-s only. Result - script doesn't close Impulse nor deletes banshee_playing. I actually can't debug the problem, but let it be. Previous version is working flawlessly if user doesn't get logged out.

Why is the usage of [[ instead of [ better when comparing?

---

