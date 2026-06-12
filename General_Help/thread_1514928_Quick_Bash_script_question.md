---
title: "Quick Bash script question"
date: 2010-06-21
forum: General Help
---

### Post by tom.swartz07 on 2010-06-21
Hi all,

I just have a really really quick question, but I cant find the answer anywhere...


Im writing a bash script that uses a for loop to call 3 commands in order depending on the input.
Specifically, the script will use the command xset to illuminate and turn off LED's on my keyboard in a specific order. IE, turn on, wait 1 second, turn off, repeat for specific number..

For some reason, I cannot get the loop to run correctly! It keeps saying that the wait is not a PID of the shell?


```
#!/bin/bash
for (( c=1; c<=$1; c++ ))
do 
	`xset led named "Scroll Lock"`;
	wait 1;
	`xset -led named "Scroll Lock"`;
done
```

Any ideas?

---

### Post by doas777 on 2010-06-21
here is some info on wait. it is "waiting" until the process with the PID listed as a parameter is done running. so you can determine the PID of your xset process and wait until it is complete. 
[http://unstableme.blogspot.com/2008/06/bash-wait-command.html](http://unstableme.blogspot.com/2008/06/bash-wait-command.html)

or did you just want to sleep for 1 second? if so, try 'sleep 1'

---

### Post by tom.swartz07 on 2010-06-21
> **doas777 said:**
> here is some info on wait. it is "waiting" until the process with the PID listed as a parameter is done running. so you can determine the PID of your xset process and wait until it is complete. 

or did you just want to sleep for 1 second? if so, try 'sleep 1'

AHA!!!

Thats the ticket!


Thank you so much! 
:D

---

