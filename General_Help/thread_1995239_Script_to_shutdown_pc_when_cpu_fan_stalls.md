---
title: "Script to shutdown pc when cpu fan stalls"
date: 2012-06-03
forum: General Help
---

### Post by EzioAuditore on 2012-06-03
Hi everyone,

So, here's my problem. My cpu fan has gone a little bit dusty and it sometimes stops in middle risking the processor.
I'll be cleaning it soon but been very busy these days. Also, I sometimes sleep with the pc running ans i can't risk my cpu.
Not in a condition to buy new one.

I've lm-sensors installed and sensors | grep fan1 shows my cpu fan's speed.
I believe that can be somehow used in a shutdown script when it stalls.
Now, I'm comfortable with the usual ubuntu stuffs but not with the bash scripting.

So i was looking for a kind of script which keeps running in the background and auto shutdown the pc when the fan stops.
Or any other workaround will also suffice but not a overkill one. :P

Thanks.

---

### Post by erind on 2012-06-03
Here is something you can start with. Add the script below, say *safe_shutdown.sh*, in the "*Startup Applications*":

*safe_shutdown.sh*

```

#!/bin/bash

while :
 do
  ## The value 100 is just an arbitrary minimum fan rpm, change it to the actual minimum fan speed. 
  if [ "$( sensors | grep -Po '(?<=^fan1:)[ \t]+[0-9]+' )" -gt [COLOR=Red]100 [/COLOR]]     
   then
    sleep [COLOR=Red]10   [/COLOR] ## Change 10 to less, if more frequent checks are needed, or viceversa.
  else
    sudo shutdown -h now
  fi
done

```Make it executable (*chmod 750 safe_shutdown.sh*), then add *shutdown* command in your sudoers file (*sudo visudo*), to avoid prompting for sudo password, when the script needs to shutdown the PC.

---

### Post by EzioAuditore on 2012-06-04
Thanks its working nice. 
Just a question, what does the sleep command does here? Does it check the fan rpm every 10 seconds?

---

### Post by erind on 2012-06-04
> **EzioAuditore said:**
> Thanks its working nice. 
Just a question, what does the sleep command does here?
The *sleep *command makes the program "sleep" for 10 secs. 

> Does it check the fan rpm every 10 seconds?It's the *sensors *command that checks the fan rpms, but *sleep *command makes the script wait for 10 secs between the checks.

---

### Post by EzioAuditore on 2012-06-04
> but sleep command makes the script wait for 10 secs between the checks.

That's what i meant actually...:P
Thanks again.

---

