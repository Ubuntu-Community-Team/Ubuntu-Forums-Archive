---
title: "Can't shutdown after using shutdown command."
date: 2012-04-05
forum: General Help
---

### Post by atomicben on 2012-04-05
Sorry for the confusing title but I couldn't really think of a better way to describe it.  Here's the deal:

I am tired of my kid leaving his damn machine on all night and day.  So, I inserted
"shutdown -h 4:00" in the /etc/rc.local file.

This really did the trick!  Now, no matter what, his computer shutsdown at 4am and stays off until he gets home from school... oh so green.

Here's the problem.  Now, if he actually does remember to try and shutdown his computer (using the gui) it doesn't work.  If I try a "sudo reboot" or "sudo shutdown now" in the terminal it says "shutdown: Another shutdown is already running"  I know I can do a shutdown -c to cancel the shutdown and then do what I need to do but my kid doesn't know the command line.  So if he wants or needs to reboot or shutdown he's out of luck.

Any ideas?  Solutions?  Is there a way for me to make the gui shutdown issue a shutdown -c and then proceed to shutdown?  Is there a completely different approach I could take?

Thanks for reading and for your help.  Have a good long weekend!

---

### Post by troymius on 2012-04-05
Can you perhaps make a script that first does "shutdown -c" followed by "shutdown -h now" and then create a desktop launcher pointing to that script?

---

### Post by atomicben on 2012-04-05
> **troymius said:**
> Can you perhaps make a script that first does "shutdown -c" followed by "shutdown -h now" and then create a desktop launcher pointing to that script?

Now that's thinking out of the box.  Great idea.  I do wish there was a way for my kid to just be able to shutdown like normal but if all else fails, this will be the way I go.  I imagine the script might have to do a gksudo to elevate but I'm not sure.  I'll have to test it out.  Thanks.

---

### Post by JC Cheloven on 2012-04-05
Your problem comes from the fact that rc.local is being executed since the startup, and hence the shutdown command it has inside. 

I guess you'd better using a cron job, so the command is executed at a fixed time, not before. Please check for example [here]("https://help.ubuntu.com/community/CronHowto") and [here]("http://askubuntu.com/questions/2368/how-do-i-setup-cron-job"). Of course come back if you need further guidance.

JC

---

### Post by galvatron408 on 2012-04-06
what's wrong with...

sudo /sbin/init 0

or

sudo halt

---

### Post by JC Cheloven on 2012-04-06
> **galvatron408 said:**
> what's wrong with...
sudo /sbin/init 0
or
sudo halt

If I at all understood, the kid forgets all the time to shut down the pc even using the standard methods...

Just to clarify: I think the OP needs to create a simple, one line, script, containing a comand which stops the system ([COLOR="Red"]shutdown -h now[/COLOR] is what I'm thinking about, others may be also possible). The script has to be executed with root privileges at a given time (I'm thinking in a cron job for that).

---

### Post by Cheesemill on 2012-04-06
> **atomicben said:**
> Now that's thinking out of the box.  Great idea.  I do wish there was a way for my kid to just be able to shutdown like normal but if all else fails, this will be the way I go.  I imagine the script might have to do a gksudo to elevate but I'm not sure.  I'll have to test it out.  Thanks.
Create the following script:
```
#!/bin/sh
sudo shutdown -c
sudo shutdown now -h
```To get round having to enter a password you can edit the sudoers file:
```
sudo visudo
```Add the following line to the bottom of the file and save:
```
ALL ALL=(ALL) NOPASSWD: /usr/bin/shutdown
```Now anyone can use 'sudo shutdown' (and therefore run the script) without having to enter a password.

---

### Post by Cheesemill on 2012-04-06
> **JC Cheloven said:**
> Your problem comes from the fact that rc.local is being executed since the startup, and hence the shutdown command it has inside. 

I guess you'd better using a cron job, so the command is executed at a fixed time, not before. Please check for example [here]("https://help.ubuntu.com/community/CronHowto") and [here]("http://askubuntu.com/questions/2368/how-do-i-setup-cron-job"). Of course come back if you need further guidance.

JC

This is an even better solution, just set a cronjob that runs 'shutdown now -h' at 4:00.
This way the normal shutdown procedure will work.

Just remember to place the entry in root's crontab so it has the correct permissions.

---

