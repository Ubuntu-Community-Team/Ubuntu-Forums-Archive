---
title: "Run a script every 2 seconds"
date: 2012-03-05
forum: General Help
---

### Post by Lockheed on 2012-03-05
I am trying to get one script to run every 2 (or 1) seconds, but how can I do it?
Cron allow 1 minute as a minimal value. I also tried something like 
```
while true ; do ./myscript & ; sleep 2; done
```
but all I get when I run it is: 
```
bash: syntax error near unexpected token `do'
```

Why do I need it to run so often? Because I need to see current CPU voltage which I get by running 
```
rdmsr -0 0x198 > /tmp/voltage 
```
and then reading the value into conky.

rdmsr requires sudo, so letting conky do it directly is not an option.

---

### Post by JCM_Pico on 2012-03-05
try using 1 instead of true... it might help ;)
```

while [ 1 ] ; do ./myscript & ; sleep 2; done
```

---

### Post by Lockheed on 2012-03-05
Hmm, same result.

---

### Post by JCM_Pico on 2012-03-05
> **Lockheed said:**
> Hmm, same result.


The problem might be in ";"

try this...

```
while [ 1 ]
do 
./myscript &
sleep 2
done
```If it works the ";" are misplaced

I think the proper use of ";" is
```

while [ 1 ]; do  ./myscript & sleep 2; done
```

---

### Post by Lockheed on 2012-03-05
Thanks, I did something similar and it's working.

---

### Post by JCM_Pico on 2012-03-05
Your welcome :) 
Happy for helping you

---

