---
title: "Two client users can't login into their sessions"
date: 2012-04-09
forum: General Help
---

### Post by Cotopaxi on 2012-04-09
Hi,

The system installed is Oneiric Ocelot.

It has three users:

User 1000, the system administrator (which is me)

User 1001, my elder son

User 1002, my younger son.

My two sons can't login into their respective sessions.

The dialog window, which asks for user-name and password comes up, both can type their data, the the system starts loading the respective desktop but hangs up during this loading.

There is an independent home partition, and every client has his own folder within this partition (I hope, I am describing it correctly). 

Can anyone give me any hint, where I can start researching (via terminal command, etc.)?

Thanks very much indeed.

---

### Post by agillator on 2012-04-09
Please describe what you mean by 'hangs up'. What does it do, how far has it come, what is showing on the screen, etc. Also, how long have you waited? 

Also take a look in your log files (/var/log/auth.log and /var/log/syslog and see if there is anything useful there. Look for things like password errors, and so on. Make sure the home partitions are actually mounted. When you are signed in try sudoing to their logins. See if you can get in that way. Let us know what you find.

---

