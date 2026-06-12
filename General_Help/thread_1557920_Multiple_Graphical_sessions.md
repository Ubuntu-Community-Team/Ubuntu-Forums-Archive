---
title: "Multiple Graphical sessions"
date: 2010-08-21
forum: General Help
---

### Post by conradin on 2010-08-21
Hi all,
I'm trying to run multiple Graphical sessions. How can I do this? I have read the forum article from 2006 but I get an error when executing startx --:2  

[http://ubuntuforums.org/showthread.php?t=185555&highlight=multiple+graphical+terminals](http://ubuntuforums.org/showthread.php?t=185555&highlight=multiple+graphical+terminals)

When I follow this howto, this is the error I get
```
 
# startx --:2

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log


```

---

### Post by dino99 on 2010-08-21
what do you mean by "multiple graphical session" ?
is it with multiple lcd or only one ?
or do you mean multiple worplaces ?

---

### Post by conradin on 2010-08-22
I mean I have 1 screen. In tty7 There is a graphic mode running under user1.
User2 wants to log into a graphical mode. How can this be done? user2 already has the ability to log in to another tty terminal, but finds it troubling to  work in a terminal mode. user1 must remain logged in / running all thier processes undisturbed.

---

### Post by spibou on 2010-08-22
> **conradin said:**
> Hi all,
I'm trying to run multiple Graphical sessions. How can I do this? I have read the forum article from 2006 but I get an error when executing startx --:2  

[http://ubuntuforums.org/showthread.php?t=185555&highlight=multiple+graphical+terminals](http://ubuntuforums.org/showthread.php?t=185555&highlight=multiple+graphical+terminals)

When I follow this howto, this is the error I get
```
 
# startx --:2
```
You must put a space between the "--" and the ":2"

---

### Post by conradin on 2010-08-23
> You must put a space between the "--" and the ":2" 

Woot!!! It works! Thank you for noticing my mistake!

---

