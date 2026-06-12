---
title: "Ubuntu 10.04 - 30 min public computer timer.."
date: 2011-04-10
forum: General Help
---

### Post by Dbqsmurf on 2011-04-10
I have a couple public computers running Ubuntu 10.04 and want timers to kick the user off after 30mins, it seems like it is the same person (not really a customer) on them everyday and not sharing them with real customers.  timeoutd is what I read but 10.04 doesn't seem to have it anymore or maybe i am missing something...

Thanks

---

### Post by Buntumatic on 2011-04-10
What exactly is keeping you from installing timeoutd?

---

### Post by scouser73 on 2011-04-10
I found this, don't know whether it's of any use to you - [[COLOR="Red"]**Install Cafe Con Leche Cyber Software in Ubuntu**[/COLOR]]("http://www.ehow.com/how_6331754_install-leche-cyber-software-ubuntu.html")

---

### Post by Dbqsmurf on 2011-04-10
> **Buntumatic said:**
> What exactly is keeping you from installing timeoutd?

How do I do this, everything I read for older ubuntu it said it was  already there and nothing says how to install..  Its been a long weekend sorry it I am just missing something...


> **scouser73 said:**
> I found this, don't know whether it's of any use to you - [[COLOR=Red]**Install Cafe Con Leche Cyber Software in Ubuntu**[/COLOR]]("http://www.ehow.com/how_6331754_install-leche-cyber-software-ubuntu.html")

I will look at this too but if there is something built in "timeoutd" wouldn't that be easier...

Thanks...

---

### Post by Krytarik on 2011-04-11
> **Dbqsmurf said:**
> How do I do this, everything I read for older ubuntu it said it was  already there and nothing says how to install..  Its been a long weekend sorry it I am just missing something...

It's in the official repos, simply run:
```
sudo apt-get install timeoutd
```
Greetings.

---

### Post by Dbqsmurf on 2011-04-15
I have timeoutd installed ubuntu 10.04 but it doesn't seem to run...

Thanks Philip

---

### Post by Dutch70 on 2011-04-15
What do you mean "it doesn't seem to run"?

Need more input! :D

---

### Post by marcosc1 on 2011-10-28
> **Dutch70 said:**
> What do you mean "it doesn't seem to run"?

Need more input! :D

Hello, I'm also having some troubles with timeoutd, it doesn't seem to work fine!

messages in syslog after idle time of user usuario:

Oct 28 12:13:49 quemlx timeoutd[18231]: User usuario exceeded idle limit (idle for 1 minutes, max=1).
Oct 28 12:13:49 quemlx timeoutd[18231]: Received SIGSEGV.. Something went wrong! Exiting!

and the timeoutd daemon stops running, and also user usuario stills loged on .

The users logs in using ssh.

I have this line in the /etc/timeouts:

Al:pts*:usuario:grupo:1:0:0:0

And running this version of ubuntu ( 10.04.3 LTS ):
root@quemlx:/var/log# uname -a
Linux quemlx 2.6.32-32-server #62-Ubuntu SMP Wed Apr 20 22:07:43 UTC 2011 x86_64 GNU/Linux


Any Idea ?
Thanks 
Marcos.

---

