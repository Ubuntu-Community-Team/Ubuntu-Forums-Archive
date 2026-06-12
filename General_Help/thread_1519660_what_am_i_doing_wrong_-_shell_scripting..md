---
title: "what am i doing wrong - shell scripting."
date: 2010-06-28
forum: General Help
---

### Post by ptrakk on 2010-06-28
i have a shell script named ics running on my startup using the command:
sh /home/ics
it is for getting my network up and running.
here is the script

#!/bin/bash
start-network
sleep 5
ifconfig eth0 192.168.3.11
sleep 3
ipmasq

it runs the start network then the sleep commands.. the problem is it doest run the other two commands (ifconfig and ipmasq). can anyone help me?
Solved and thanks for all the help! :D

---

### Post by xsinsx on 2010-06-28
Im going to take a stab in the dark and guess that maybe your eth0 is not up yet so you would have to have something that looked like this. 

```
[color=#408080][i]#!/bin/bash
[/i][/color]start-network
sleep 5
ifconfig eth0 up
ifconfig eth0 192.168.3.11
sleep 3
ipmasq

``` 

I am not positive but you might try that.

---

### Post by ptrakk on 2010-06-28
ok heres the thing.. it works sometimes. i dont see a pattern in it. sometimes the ethernet does come up, but it seems to be ignoring some commands. ive added longer sleep commands but nothing changes.

---

### Post by ptrakk on 2010-06-29
i just had a thought to maybe use semicolons.. it worked!

---

### Post by MooPi on 2010-06-29
Can you post your final script for us ?

---

### Post by ptrakk on 2010-06-29
> **MooPi said:**
> Can you post your final script for us ?

sure thing!
```

#!/bin/bash
/usr/bin/start-network;
sleep 9;
/sbin/ifconfig eth0 192.168.3.11 up;
echo "ifconfig done and network configured";
sleep 9;
/usr/sbin/ipmasq;
echo all done;
sleep 2;

```

---

### Post by ptrakk on 2010-06-29
okay it worked a couple times but didnt the third time

im gonna try 
```

#!/bin/bash
exec /usr/bin/start-network;
sleep 9;
exec /sbin/ifconfig eth0 192.168.3.11;
echo "ifconfig done and network configured";
sleep 9;
exec /usr/sbin/ipmasq;
echo "all done";
sleep 2;

```

with the exec commands.. i have to wait for the roomate to have a break on the internet.

---

### Post by ptrakk on 2010-06-29
got it working finally.. still dont know what was wrong with my other script.. here is the working code. im using intrepid also


```

#!/bin/bash
/usr/bin/start-network && sleep 9 && /sbin/ifconfig eth0 192.168.3.11 && echo "ifconfig done and network configured" && sleep 9 && /usr/sbin/ipmasq && echo "all done" && sleep 2

```

---

