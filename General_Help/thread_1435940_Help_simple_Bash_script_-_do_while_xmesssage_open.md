---
title: "Help simple Bash script - do while xmesssage open"
date: 2010-03-22
forum: General Help
---

### Post by Ventil on 2010-03-22
Hi,

I need something to popup a xmessage and play a .wav file every 120sec until I close xmessage. How can I do that?

This is not working obviously
```
#!/bin/bash

xmessage -center Website is updated
while [ xmessage = true ]
do
   aplay ~/Downloads/mail_here.wav
done
```

---

### Post by prodigy_ on 2010-03-22
Try this:

```
#!/bin/bash

xmessage -center Website is updated &
XM_PID="$!"
while [ x"$(ps ax -o pid|grep " $XM_PID")" != x"" ]
do
  aplay ~/Downloads/mail_here.wav
  sleep 120
done
```

---

### Post by Ventil on 2010-03-22
Wow. Works just like I needed. 
Thanks a lot prodigy_!

---

### Post by prodigy_ on 2010-03-22
Np. :-)

---

### Post by Ventil on 2010-03-22
I wonder what this does though

```
XM_PID="$!"
while [ x"$(ps ax -o pid|grep " $XM_PID")" != x"" ]
```

---

### Post by prodigy_ on 2010-03-22
> **Ventil said:**
> I wonder what this does though
XM_PID= stores the PID of background process (xmessage) in a variable that can be checked later. (It's possible to skip this step but one day I had a horrible debugging experience with $?, when I was trying to check the return code of some function. Since then I prefer to play safely.)

While statement checks if variable $(ps ax -o pid|grep " $XM_PID") is or isn't empty. The value of this variable equals to the output of the command placed inside the parentheses. Finally, the command tries to find the stored PID among the PIDs of all currently running processes.

---

### Post by Ventil on 2010-03-22
OK. I understand now. Thanks again prodigy_

---

