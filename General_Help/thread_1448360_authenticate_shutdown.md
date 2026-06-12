---
title: "authenticate shutdown"
date: 2010-04-06
forum: General Help
---

### Post by strattonbrazil on 2010-04-06
I installed a few media servers to stream something to my PS3 over the weekend, but now when trying to shutdown the computer, I'm asked to authenticate with a password since other users are still logged in.  I installed quite a few programs over the weekend trying to get it to work, so I can't remove a specific one.  Is there a way to see which daemons are logged in under a different session?

Edit: Found it using the tips below.  It turned out to be mythtv.  Thanks.

---

### Post by cjhabs on 2010-04-06
> **strattonbrazil said:**
> I installed a few media servers to stream something to my PS3 over the weekend, but now when trying to shutdown the computer, I'm asked to authenticate with a password since other users are still logged in.  I installed quite a few programs over the weekend trying to get it to work, so I can't remove a specific one.  Is there a way to see which daemons are logged in under a different session?

```

ps -elf | grep username

```
where username is the user you wish to check the processes for.

---

### Post by strattonbrazil on 2010-04-06
Well, I've done that already but that gives a whole lot of programs to search through.  Is there something that specifically shows processes on another session?  

When I type in 'users', I get my username twice if that makes any difference.

---

### Post by cjhabs on 2010-04-06
Ok - I see.

If you run "who" you will see which sessions are running - pts are pseudo terminals running in your physical session - ttyx are real console sessions.

However, I don't know how to track down what processes run under a different session - maybe the "ppid" column of "ps -elf" will tell you - you can find the controlling process id with "ps -elf | grep ttyx"

---

