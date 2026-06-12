---
title: "Where to define the shutdown time? Minimum recommended?"
date: 2010-01-13
forum: General Help
---

### Post by pstein on 2010-01-13
When I shutdown Ubuntua dialog popup tells me that shutdown will take place in 60 seconds.
 
How can I decrease this number of seconds?
 
What is the minimum recommended?
 
Is 5 seconds sufficient if I run no servers?
 
Peter

---

### Post by VCoolio on 2010-01-13
You can disable in gconf-editor, at /apps/indicator-session/suppress_logout_shutdown. I'm not sure if you can reduce time.

---

### Post by pstein on 2010-01-14
> **VCoolio said:**
> You can disable in gconf-editor, at /apps/indicator-session/suppress_logout_shutdown. I'm not sure if you can reduce time.
 
How do I access "gconf-editor"?

---

### Post by wojox on 2010-01-14
Open a terminal Applications > Accessories > Terminal and run this:

```
gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool true
```

It will turn it off.

Or gconf is Alt + F2 gconf-editor

---

### Post by audiomick on 2010-01-14
Hallo.
I suspect that the time can only be an increment of whole minutes. I believe the shutdown button evokes the " shutdown" command. A look at
```
man shutdown
```
shows the following
 > 
  shutdown [OPTION]...  TIME [MESSAGE]
shutdown arranges for the system to be brought down in a safe way.  All logged-in users are notified that the system is going down and, within the last five minutes of TIME, new logins are prevented.

TIME  may  have  different  formats, the most common is simply the word 'now' which will bring the system down immediately.  Other  valid  formats  are  +m,  where m is the number of minutes to wait until shutting   down and hh:mm which specifies the time on the 24hr clock.

It doesn't look like there is provision for less than a whole minute.

---

