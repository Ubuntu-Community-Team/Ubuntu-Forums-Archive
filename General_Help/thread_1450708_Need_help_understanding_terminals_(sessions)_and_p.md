---
title: "Need help understanding terminals (sessions?) and processes assigned to them."
date: 2010-04-09
forum: General Help
---

### Post by lumix on 2010-04-09
*This is not a multimedia question, but an enquiry about how processes and sessions interact that came about from the following multimedia setup.*

Something curious happened while setting up a home-grown media server.  I have an ubuntu 9.something installation--sans desktop environment--that launches lirc and irexec from /etc/rc2.d/S99irexec. After booting (but not logging in) I can launch programs from the remote (via irexec, of course).  But if I launch mplayer, while it does start and play, it does not get picked up by lircd as a client--no input such as pause, forward, next, etc. will work.

*However*, if I then log in as root, terminate both irexec and mplayer, run /etc/rc2.d/S99irexec, and log off again, I can then launch mplayer (again, through irexec), whereupon lircd *does* pick up mplayer and works happily.

So why would lircd interact fine with mplayer when the command chain is:
*logged-root-->S99irexec-->mplayer*
but not interact with mplayer when the chain is:
*system-boot-up-->S99irexec-->mplayer*?

---

