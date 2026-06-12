---
title: "Can't see results of job scheduled with the 'at' command"
date: 2010-10-05
forum: General Help
---

### Post by husky8 on 2010-10-05
Hi,
 
I am a new Linux and Ubuntu user.  I scheduled a job, 'ls -a', with the at command, 3 minutes in the future.  It looks like the job ran, but I cannot see the results of 'ls -a'.  I accessed my mail with the 'mail' command and saw that the output of my scheduled job was message 1.  I typed in '1' after the & prompt, and saw that the subject of the message was the output of my job, scheduled at the time specified with the 'at' command.  I cannot see the output of the 'ls -a' command that I scheduled though.  How do I see the contents of the message, and the actual output of the job.
 
Thank you

---

### Post by ridgeland on 2010-10-06
I would not expect to "see" the results of "ls -a" except in the terminal that ran it.
I use cron jobs not at jobs but when I need output from such a command I send it to a text file like:
ls -a > /home/me/lsa.txt

---

