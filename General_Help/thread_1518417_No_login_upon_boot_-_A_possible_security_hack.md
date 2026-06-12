---
title: "No login upon boot - A possible security hack?"
date: 2010-06-26
forum: General Help
---

### Post by bootbat on 2010-06-26
Hi Friends,

I am facing a strange issue here. I do not seem to get the login screen when Ubuntu 10.10 boots up. Under "Users and Groups", it seems to be set to ask for a password when booting up. Also, sometimes when I try to run the update manager, it says that the it could not lock the var directory although I have only Firefox running (no apt-get running). At one time when I tried to reboot the system, it mentioned that other users are logged in although  I have just one user created in this installation. I am a little confused and wanted to get some tips on why this might be happening. Is it possible that my system has been hacked into?

---

### Post by dabl on 2010-06-26
> **bootbat said:**
> Hi Friends,

I am a little confused and wanted to get some tips on why this might be happening.



I'd say the main reason you are seeing performance problems is that you are running an Alpha version of Ubuntu -- it is not even considered sufficiently developed for general testing.  You are seeing development bugs, in all likelihood.

---

### Post by bootbat on 2010-06-26
Ops...did I mention I was using 10.10? It's actually 10.04 - Lucid. Sorry for the misdirection.

---

### Post by bootbat on 2010-06-28
Hi Friends,

Some pointers on this issue will be great. Unfortunately, I have not been able to get anything related to this in the forums yet.

---

### Post by bootbat on 2010-07-17
This issue remains unresolved till date. Is there anyone out there who can point me in the right direction?

---

### Post by The Cog on 2010-07-17
For your login screen issue, the option to automatically log a user in is located in System->Administration->Login Screen I guess it must be configured to log you in automatically there.

The only time I have seen "other users" warnings is when I have also been logged in either on a tty console or over an SSH remote session. The command "w" will show who is logged in and what program they are running.

---

