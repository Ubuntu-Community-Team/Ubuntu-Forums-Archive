---
title: "How do I remotely kick off a 100% automated system update?"
date: 2011-06-17
forum: General Help
---

### Post by michwill on 2011-06-17
Hi All,

I have a client that needs 5 machines updated.  They are all running Ubuntu 9.04.  Long story short, I can only log in over VPN for the time being (as they're in another city).

That said, is there any good way to remotely update the systems without the need to remain logged in (e.g. via SSH)?  I'd like to simply kick off the updates and check back in at a later time.

Best.

---

### Post by tgm4883 on 2011-06-17
> **michwill said:**
> Hi All,

I have a client that needs 5 machines updated.  They are all running Ubuntu 9.04.  Long story short, I can only log in over VPN for the time being (as they're in another city).

That said, is there any good way to remotely update the systems without the need to remain logged in (e.g. via SSH)?  I'd like to simply kick off the updates and check back in at a later time.

Best.

Use screen.

---

### Post by crispy_420 on 2011-06-18
Scheduled cron jobs should do the job, right?

---

### Post by michwill on 2011-06-18
> **tgm4883 said:**
> Use screen.


Could you be a little more verbose?  The "Remote Desktop" service is not enabled on any of the machines.  Also, two of them are just running Ubuntu Server (I suppose I should have mentioned that).

---

### Post by michwill on 2011-06-18
> **crispy_420 said:**
> Scheduled cron jobs should do the job, right?


I've never used cron for system updates.  I suppose we'll find out. [-o<

---

### Post by tgm4883 on 2011-06-18
> **michwill said:**
> Could you be a little more verbose?  The "Remote Desktop" service is not enabled on any of the machines.  Also, two of them are just running Ubuntu Server (I suppose I should have mentioned that).

There is a utility called 'screen' (man screen) that is for exactly what you want to do. It's a command line utility useful for when you want to logout but continue running whatever you were doing in your session. These links may be beneficial for you

[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)
[http://ss64.com/bash/screen.html](http://ss64.com/bash/screen.html)

---

### Post by michwill on 2011-06-19
> **tgm4883 said:**
> There is a utility called 'screen' (man screen) that is for exactly what you want to do. It's a command line utility useful for when you want to logout but continue running whatever you were doing in your session.

Awesome.  Incidentally, I believe NOHUP was a viable option too.  Thanks!

---

