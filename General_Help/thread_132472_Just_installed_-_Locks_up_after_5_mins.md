---
title: "Just installed - Locks up after 5 mins ?"
date: 2006-02-18
forum: General Help
---

### Post by synergynova on 2006-02-18
I've just installed ubuntu 5.10 from the distributed cd.

It seems to be locking up after about 5 mins running...
Both when logged in and at the log in screen.

Any ideas?
Woody

---

### Post by tgbp492 on 2006-02-18
Are you getting any error messages?  In the time that it will work and have you been able to view any .logs?

Big Tim

---

### Post by synergynova on 2006-02-18
No error messages.  I had no issues with the Live disc running ubuntu.
I should be able to get the error log.  I'm new to ubuntu where can I get these from?

---

### Post by synergynova on 2006-02-18
Just re-installed ubuntu and now I just get a blank screen where before I got the logon screen?  Any idea?
I tried going in to equivilent to safe mode which takes you to a command prompt but I didn't really have a clue what to do from there.  I managed to login and out.

---

### Post by nalmeth on 2006-02-18
Do you have a special video card? In terminal safe mode, type:

sudo dpkg-reconfigure xserver-xorg 

select defaults everywhere, but when selecting video driver pick 'vesa'

---

### Post by synergynova on 2006-02-18
Ok thanks, I'll try that.  It's just odd as it was displaying fine?

Cool that seems to have fixed it, thanks...
Any ideas why I can't get into the services, will I have to login as adminstrator?

---

