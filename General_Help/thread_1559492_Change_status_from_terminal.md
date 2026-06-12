---
title: "Change status from terminal"
date: 2010-08-23
forum: General Help
---

### Post by Altay_H on 2010-08-23
I'd like to write a script that changes my status for me. However, the only way I know how to change my status is to use the Indicator Applet Session. Is there a way to change my status from the command line so that I can incorporate it into a script?

---

### Post by Old *ix Geek on 2010-08-23
I literally just woke up from a nap, and I'm working on a nice cup of coffee, but...I have no idea what you're talking about. Change your status where? And change it from what to what? There's pretty much nothing that can't be done in a *nix script, so it's just a matter of sorting out what exactly you're trying to do.

---

### Post by Altay_H on 2010-08-23
> **Old *ix Geek said:**
> Change your status where?
On the right-most corner of the top bar in Ubuntu your username is displayed. If you click it, it will allow you to change your status. This change applies to all IM clients: Empathy, Pidgin, Skype, etc. It's a simple way to set your status on all IM clients.

> **Old *ix Geek said:**
> And change it from what to what?
From Available to Invisible or vice versa usually.

---

### Post by sillyfofilly on 2010-08-29
I am interested in doing something similar to this. The part where your username is displayed in Ubuntu is called the "Me Menu" and is contained in the package indicator-me

Unfortunately that's all I can add, since I have yet to find a way to hook into this application to change status.

---

### Post by samg34 on 2011-08-14
**You can not change the status from terminal with empathy**. **This is why I am switching to Pidgin**. I want Empathy to start "available" when i log in. Empathy starts as "offline" which means I would build a start-up script to turn it to "available" unfortunately you can not do this in terminal, so whenever Empathy starts it will always be "offline" and I can't do anything about it except try to rewrite the code (UGHH). This is why I am switching to pidgin. With Pidgin you can use 
$ purple-remote "setstatus?status=away&message=AFK"
Better yet, for my purpose, pidgin will remember the last status you chose and change it to that on login. So for my purpose, I don't even need a start-up script. **But for all purposes, Pidgin does let you change the statu**s.

---

### Post by samg34 on 2011-08-14
[http://telepathy.freedesktop.org/doc/book/sect.connection.presence.html](http://telepathy.freedesktop.org/doc/book/sect.connection.presence.html)
The link goes to a page that shows the python API for setting the connection. I am working on making a patch for emapthy. I will show you when I am done.

---

