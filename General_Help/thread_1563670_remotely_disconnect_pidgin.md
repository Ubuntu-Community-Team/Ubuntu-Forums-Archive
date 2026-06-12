---
title: "remotely disconnect pidgin?"
date: 2010-08-29
forum: General Help
---

### Post by varonbondumb on 2010-08-29
the situation:  i have 2 computers.  both have pidgin messenger  with the same accounts (yahoo, msn, aim, facebook...).  both can connect at the same time.  both connect at startup.  both work well.  some of the chat protocols disconnect upon sensing multiple connections (as in, when one account signs in from two places).  good.  others don't.  bad.

which is where my question comes in:
is there a way to remotely disconnect the OTHER computer's pidgin while using the current computer?  while both instances of pidgin are running, the OTHER computer will see all incoming messages on pidgin.  anyone at that computer will see a one-sided conversation.

simple solution would be to stop them from connecting at startup.  that still doesn't solves the problem of "what if i forgot to turn one off" or "what if someone runs pidgin on the other computer."

if not pidgin, then what about empathy (yuck)?

---

### Post by Pollox on 2010-08-29
Do you currently have a way to remotely connect to the other computer?  For example, if you can ssh into it, you could then execute "killall pidgin" to stop pidgin on the remote computer.

---

### Post by varonbondumb on 2010-08-30
> **Pollox said:**
> Do you currently have a way to remotely connect to the other computer?  For example, if you can ssh into it, you could then execute "killall pidgin" to stop pidgin on the remote computer.

a brilliant idea!  anyone know the best way to remotely connect to a computer before i go stumbling through ubuntuforums like a monkey looking at a math problem?

---

### Post by Pollox on 2010-08-30
> **varonbondumb said:**
> a brilliant idea!  anyone know the best way to remotely connect to a computer before i go stumbling through ubuntuforums like a monkey looking at a math problem?

[ssh]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html") is the best way in my opinion.  Don't be scared off by the amount of documentation on the page, since most of it is optional configuration stuff.  You could also look at [VNC]("https://help.ubuntu.com/community/VNC"), which lets you remotely view your desktop, but it looks like it requires you to set up ssh first anyway.

---

### Post by varonbondumb on 2010-08-31
thanks!

---

