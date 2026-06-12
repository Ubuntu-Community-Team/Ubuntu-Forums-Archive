---
title: "Password/Login Problems"
date: 2009-08-06
forum: General Help
---

### Post by bubba1358 on 2009-08-06
Using Ubuntu Desktop 8.04. I have all packages updated as of today. I am currently having two separate issues involving passwords:
 
1. When I log on, after entering my password I get a message saying "No logon servers." I then an forced to re-enter my password, and get a error message simply saying "Error." After the "Error" everything loads fine. Thisa only happens with my one local account (see more info below).
 
2. I am trying to add a new user using the Users and Groups GUI. The "Add User" button is currently grayed out. The whole system hangs when I attempt to use the Unlock feature. I enter my password, and then it just hangs. The mouse moves, but no windows respond. I am forced to hard-reboot the system (reset button on the case) to recover functionality.
 
Other noteworthy things:
* I have successfully joined to an AD domain via this guide: [http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)
* Curiously, logging in as a user via a domain account does NOT cause the initial login error carousel. It pops right up and works great.
* I have WINE (stable version, not beta) installed and functional.
 
My end goal here is to convert the 140-or-so computers in the elementary school where I work from Windows XP to Ubuntu over the next few years. I am planning to run an experiment with about 10 machines this year, and see how it goes. This is the first test system I have. It ultimately needs to run as a client accessing M$ Server 2008. I want it to be able to access shares, log in via AD authentication, run as an email client, and print over the Windows network. Unfortunately, this Users and Groups thing is really stalling progress.
 
Thanks, in advance, for any help you can provide,
 
~Matt

---

### Post by bubba1358 on 2009-08-07
bump

---

### Post by martinbaselier on 2009-08-07
I guess one of the adjustments you made is causing problems. 

Try: 
**dmesg | less**
to check if there are any kernel errors related to your problem. 

Your log files in /var/log/ might shed some light on the cause of this problem.

---

### Post by bubba1358 on 2009-08-07
Thanks.  I was not able to really find anything useful before it stopping booting altogether.  No worries, it was a prototype I can quickly rebuild.  At least I know where to go if it happens again!
 
Thanks again!

---

