---
title: "How to send SIGINT to a bash script"
date: 2009-09-09
forum: General Help
---

### Post by stair314 on 2009-09-09
I'm writing a bash script that I'd like to be able to run in the background and later send a SIGINT signal. Unfortunately I'm unable to get the address of the script when I run it in the background. For example, if I have a file called "bashtest.sh" consisting of 
> 
#!/bin/bash
echo $$

this is what happens when I run it
> 
user@host:~$ ./bashtest.sh 
32688
user@host:~$ echo $!
32672

So the PID that I have access to is just the PID of the bash interpreter, and the script itself gets a different PID, thereby preventing me from sending it the SIGINT signal (sending it to bash doesn't work). Is there a way of getting the PID of the script itself, short of modifying every script I want to use in this way to save its PID to file?

---

### Post by Locutus_of_Borg on 2009-09-09
kill -9 `ps aux|grep bashtest.sh|awk '{print ($2)}'`

---

### Post by Locutus_of_Borg on 2009-09-09
```
kill -9 `ps aux|grep bashtest.sh|awk '{print ($2)}'`
```


i swear i replied to this already, and then my post disappeared, it remained in my history though...did someone delete this for some unknown reason?

---

### Post by stair314 on 2009-09-09
I got the e-mail for your original post so you definitely did put one there. I'm not sure what happened to it.

That won't help though. kill -9 sends SIGKILL. SIGKILL will indeed bring down my script but I want to be able to trap the signal and respond to it. SIGKILL is untrappable.

---

### Post by Bachstelze on 2009-09-09
I deleted it, for the reason stair314 just pointed out. kill -9 will send SIGKILL, not SIGINT. Fortunately, stair314 knew that, but if he didn't and had blindly ran your command, it could've been bad.

If you are not sure of what you are posting, please just post nothing instead of potentially malicious commands.

---

### Post by stair314 on 2009-09-09
Turns out I was barking up the wrong tree before. If I run my script **in the background** like I want to, then the issue I found with that test case above goes away.

If I use this test script
> 
#!/bin/bash
trap "echo 'got me!'" 2
echo $$
while [ 1 ]
do
        sleep 1;
        echo "alive"
done

and run it in the background, everything works fine, but if I have it sleep for longer it quits responding to signals. Is it impossible to trap signals while sleeping?

---

### Post by stair314 on 2009-09-09
By the way, in defense of Locutus_of_Borg, the kill -9 command wouldn't have hurt anything since it was written to target my test script.

---

### Post by stair314 on 2009-09-09
> 
while [ 1 ]; do kill -INT 1041; done

will do the job, where 1041 is the PID I'm trying to hit. Is there a different version of sleep that wouldn't require me to do this? Or some way to send a signal that would be received on wakeup?

---

