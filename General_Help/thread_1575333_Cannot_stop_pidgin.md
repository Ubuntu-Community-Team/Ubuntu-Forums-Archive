---
title: "Cannot stop pidgin"
date: 2010-09-15
forum: General Help
---

### Post by russpet on 2010-09-15
Hello.   I have pidgin 2.6.6 installed on Ubuntu 10.04.  (64 bit box)

My pidgin app is intercepting incoming chats -- even when I have pidgin closed down.  (because I'm using another machine for chatting.)  

I've checked startup applications.
I've ensured I haven't told Ubuntu to remember open applications when I log out.
"ps -ef | grep pidgin" gives no app running.

Seems a daemon is running that I can't track down.  
It's very annoying for my linux box to intercept my chats when I'm logged in on another machine in another location.  

Thanks,
Russ

---

### Post by TwelveGauge on 2010-09-15
terminal: 
```
ps ax
#look for the number in the SECOND column from the left that corresponds to pidgin 
kill -9 <number>
```

additionally, why don't you just get rid of pidgin?

---

### Post by russpet on 2010-09-15
> **TwelveGauge said:**
> terminal: 
```
ps ax
#look for the number in the SECOND column from the left that corresponds to pidgin 
kill -9 <number>
```additionally, why don't you just get rid of pidgin?
Thanks will try the "ax" version of "ps".  Is there another built in chat program for ubuntu for connecting to Microsoft Communicator sessions - that you recommend?

---

