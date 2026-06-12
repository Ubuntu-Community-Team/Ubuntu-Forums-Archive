---
title: "Quick BASH Scripting help"
date: 2009-12-14
forum: General Help
---

### Post by aspiredfang on 2009-12-14
Hello fellow Ubuntu peoples, I was please wondering if someone could enlighten me to a problem I'm having with a simple script file. I'm quite new to Linux and trying to make it so that the script will detect if a version of Cairo-Dock is already running and if not to start one. This is necessary as when logging off with sessions saved, it will just go and recreate a new one. Looking around, other peoples solutions have just been to disable session saving but to me, this isn't a fix :P

Coming from a background in PHP, I would normally run the 'ps...' command in the selection statement itself and test for false with a simple "!" but, bash cried about it being improper syntax? I've had a look around the net and here's what I have come up with. Help with the actual syntax would be appreciated if the script can be shortened to performing the above in the selection line also. As it stands, the condition is always true and Cairo-dock will launch another instance even if the $check variable is not empty. :sad:

- Make variable $check a list of any running processes matching the literal 'cairo-dock -c'
- perform check on variable to see if it is empty
- If empty run command 'cairo-dock -c'

     ```

#Cairo-start.sh 
$check = ps aux | grep 'cairo-dock -c';  
if [$check = '']  then
   cairo-dock -c 
fi

```Kudos and thanks in advance for any response

---

### Post by Brandon Williams on 2009-12-15
> **aspiredfang said:**
> ```
#Cairo-start.sh 
$check = ps aux | grep 'cairo-dock -c';  
if [$check = '']  then
   cairo-dock -c 
fi
```

In bash, you only use the '$' when you want to get the value of the variable. Also,  if you want to store command output in a variable, you will enclose it in '$( cmd )'. Next, spacing is very important: no spaces around the '=' in an assignment, but spaces on both sides of '[' and ']' in a condition. And finally, a variable that might have multiple tokens in its value should be quoted.

```
#Cairo-start.sh 
check=$(ps aux | grep 'cairo-dock -c')
if [ -z "$check" ]; then
   cairo-dock -c 
fi
```

All of that said, it's possible that your script is not running with bash, since you didn't specify bash as the interpreter. This could be why the '!' isn't working. Try this:

```
#!/bin/bash
if ! ps -C cairo-dock > /dev/null
then
    cairo-dock -c
fi
```

---

### Post by aspiredfang on 2009-12-15
Thanks a lot for the reply Brandon, filled in multiple pieces of missing knowledge when it comes to bash scripting which didn't stand out on some of the guides I had read.

A fan of the "/dev/null" to pass the ps command silently in to the script and using the -C operator on ps. I feel enlightened and will be digging deeper in to any functions used before making a messy script as mine was. *shy*

Again, Kudos and thanks be to you

---

