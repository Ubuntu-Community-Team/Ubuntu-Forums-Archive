---
title: "Why does &quot;lastlog&quot; show &quot;never logged in&quot; for ALL users?"
date: 2010-07-12
forum: General Help
---

### Post by pstein on 2010-07-12
From Solaris I know a command "lastlog" which shows the times when each existing user logged in the last time.
 
When I enter the same command in Ubuntu then it is executed (=it must exist) but for all users "** Never logged in **" is displayed although of cause at least the current user must be logged in some time.
 
Do I have to enable this kind of logging somehow?
 
How exactly ?
 
Peter

---

### Post by yetiman64 on 2010-07-12
Using that command gives output as you say for me as well, except for my user account. It shows me to have logged into a tty terminal and the time and date of such.

Try logging into a tty terminal CTRL + ALT + F(1-6), enter your username and password, then type exit and go back to tty7 with CTRL + ALT + F7 ie back to your desktop.

Rerun the lastlog command and note the difference for your username.

I note it only seems to be logging logins on the tty terminals and not X logins (or gnome).

---

### Post by pstein on 2010-07-22
I tried out your suggestions but it still always shows 
 
** Never logged in**
 
I guess I have to enable login/logout auditing at first.
 
How do I do that?
 
Peter

---

### Post by yetiman64 on 2010-07-22
> I guess I have to enable login/logout auditing at first.
 

Never had to enable it here (on Lucid at the moment but noted the behaviour going back to Hardy Heron), it has always just worked for tty terminal logging for me.

I'm unsure of your situation. Anyone else ever notice this ?

---

### Post by no2498 on 2010-07-23
tty1                      Sun Apr 26 10:29:59 -0400 2009


all the rest was never logged in

must not use that very often

---

### Post by bodhi.zazen on 2010-07-23
> **pstein said:**
> I tried out your suggestions but it still always shows 
 
** Never logged in**
 
I guess I have to enable login/logout auditing at first.
 
How do I do that?
 
Peter

Most of the users in that list are system users / daemons and in fact should never have logged in.

Use ```
lastlog | grep -v Never
```

Or specify a user if you like.

---

