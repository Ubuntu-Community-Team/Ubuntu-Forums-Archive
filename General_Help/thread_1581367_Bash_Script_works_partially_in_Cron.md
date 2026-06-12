---
title: "Bash Script works partially in Cron"
date: 2010-09-24
forum: General Help
---

### Post by jimestesphl on 2010-09-24
Hi,
I have a script that pops up a jpg file several times a day as a reminder. The script is called up by crontab and it works perfectly. 
The issue is that I want the script to also perform a system "beep" in addition to popping up the jpg file. When I test it on the command line everything works but when I run it in cron the jpg file pops up but the beep doesn't beep.  

I'm thinking the problem is in the "echo -e \\a" part. I must be missing something.  Thanks for the help. 

Here is my script:

#!/bin/bash
echo -e \\a
sleep01; echo -e \\a
sleep01; echo -e \\a
xterm -hold -display lxstn02:0.0 -exec -g 600x900-0-0 eog /home/etms/my_cron/phl.jpg

---

### Post by Aaron5367 on 2010-09-24
Can we see your crontab setup? Also, have you tried one slash?

---

### Post by mobilediesel on 2010-09-24
> **jimestesphl said:**
> Hi,
I have a script that pops up a jpg file several times a day as a reminder. The script is called up by crontab and it works perfectly. 
The issue is that I want the script to also perform a system "beep" in addition to popping up the jpg file. When I test it on the command line everything works but when I run it in cron the jpg file pops up but the beep doesn't beep.  

I'm thinking the problem is in the "echo -e \\a" part. I must be missing something.  Thanks for the help. 

Here is my script:

#!/bin/bash
echo -e \\a
sleep01; echo -e \\a
sleep01; echo -e \\a
xterm -hold -display lxstn02:0.0 -exec -g 600x900-0-0 eog /home/etms/my_cron/phl.jpg

I don't think that method works for beeping via cron as I believe it has to be in an actual terminal. You could install the **beep** command which would work from cron.
you would just use
```
beep
```
instead of ```
echo -e \\a
```

---

### Post by jimestesphl on 2010-09-25
Thanks for the reply.  Here is my cron:
10 11,13,15,17,19,21,,23,01 * * * /home/etms/my_cron/telcon_remind
10 16 * * 1,2,3,4,5 /home/etms/my_cron/phl_daily_remind
22 14 * * 1,2,3,4,5 /home/etms/my_cron/netelcon_remind
15 16 * * 1,2,3,4,5 /home/etms/my_cron/start_talking

I did try it with one slash but it didn't work.  Interestingly, when I tested one slash on the command line there was no beep but I did get "a" returned 3 times in the terminal window.

Unfortunately, this is a work computer and I cannot install the "beep" command because I cannot sign in as root.

The other thing I tried was to alias the "echo -e \\a" command but that still didn't work in cron.

---

### Post by dcstar on 2010-09-26
> **jimestesphl said:**
> Hi,
I have a script that pops up a jpg file several times a day as a reminder. The script is called up by crontab and it works perfectly. 
The issue is that I want the script to also perform a system "beep" in addition to popping up the jpg file. When I test it on the command line everything works but when I run it in cron the jpg file pops up **but the beep doesn't beep**.  
.........

Of course not, when CRON runs the job it has no idea where to output any beep because it cannot assume just because you may have a terminal running that is where it is supposed to output it to.

Explicitly set the output of any shell commands you run in cron, or simply uses tools like aplay to output sound to the default device in the system.

---

### Post by jimestesphl on 2010-09-26
David,
Thank you for the reply.  What you said makes sense but how do I explicitly set the output of the shell command?  Can you give me an example?

---

### Post by jimestesphl on 2010-09-26
I found the answer!!  Thanks guys for helping me out with this.  I found out how to make the computer beep from the console and now my script works from cron just like I wanted it to.
Here is my improved script:

#!/bin/bash
[COLOR="Red"]echo -en "\a" > /dev/console/
sleep01; echo -en "\a" > /dev/console/
sleep01; echo -en "\a" > /dev/console/[/COLOR]
xterm -hold -display lxstn02:0.0 -exec -g 600x900-0-0 eog /home/etms/my_cron/phl.jpg

Thanks again.

---

### Post by btindie on 2010-09-26
When cron runs your script its STDOUT handle would point to a file/syslog and not a character device (console) and so no beep would be heard.

---

### Post by jimestesphl on 2010-09-26
Thanks for the explanation.  I'm really new at this and appreciate the help.

---

