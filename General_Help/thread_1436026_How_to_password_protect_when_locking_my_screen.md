---
title: "How to password protect when locking my screen"
date: 2010-03-22
forum: General Help
---

### Post by musabg on 2010-03-22
Hello,  When I press ctrl+Alt+L to lock my screen and walk away, I come back, move the mouse and I'm simply in !!!  how can I put a password when I lock my computer.  Thanks, Musab

---

### Post by bobcollard on 2010-03-22
> **musabg said:**
> Hello,  When I press ctrl+Alt+L to lock my screen and walk away, I come back, move the mouse and I'm simply in !!!  how can I put a password when I lock my computer.  Thanks, Musab
Open Screensaver and check the box for "Lock Screen When Screensaver Active."

---

### Post by musabg on 2010-03-22
> **bobcollard said:**
> Open Screensaver and check the box for "Lock Screen When Screensaver Active."

Thanks for your reply..

I did this already ... BTW I'm logged in as root. 

Yes I enabled my root user.

Any idea ?

---

### Post by Hikayu on 2010-03-22
> **musabg said:**
> Thanks for your reply..

I did this already ... BTW I'm logged in as root. 

Yes I enabled my root user.

Any idea ?

You shouldn't log in as root...

You need to set a password for root then. 

System > Administration > Users and Groups

Select root and enter new password,


Cheers,
Hikayu

---

### Post by bobcollard on 2010-03-22
> **musabg said:**
> Thanks for your reply..

I did this already ... BTW I'm logged in as root. 

Yes I enabled my root user.

Any idea ?
Not a good idea unless you are changing things like config files.  There are warnings about that.  As root you are always able to connect to anything.  That may be why it does not lock.

---

### Post by musabg on 2010-03-22
**[COLOR=blue]I had to login as root to avoid some problems I was facing during the installation of (KOHA integrated library system, mysql server, apache server, tork and other softwares) they won't install properly unless I login as root.[/COLOR]**
**[COLOR=blue][/COLOR]** 
**[COLOR=blue]but that's true...when I use the other user I can lock the screen. So basically I cannot lock it while using the root , I see. no big deal I was just tetsing this cool idea here[/COLOR]**
**[COLOR=blue][/COLOR]** 
[**[COLOR=blue]http://ubuntuforums.org/showthread.php?t=702372[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=702372")
**[COLOR=blue][/COLOR]** 
**[COLOR=blue][/COLOR]** 
**[COLOR=blue]Thanks guys.[/COLOR]**
**[COLOR=blue]-Musab[/COLOR]**
**[COLOR=blue][/COLOR]**

---

