---
title: "remove Suspend and Hybernate from menus"
date: 2011-08-30
forum: General Help
---

### Post by deserthowler on 2011-08-30
I sometimes have guest users on my computer.  Before any problems start, I want to remove Suspend and Hybernate from the possible menu choices.

I'm using Ubuntu 10.04 LTS and 11.04

Earl

---

### Post by CatKiller on 2011-08-30
Not at my computer at the moment, but I seem to remember seeing a GConf key that controlled whether that was available.

You could probably also do something with permissions if you created a guest account.

---

### Post by angry_johnnie on 2011-08-30
the keys are there:

apps/gnome-power-manager/general

can_suspend

and

can_hibernate


supposedly, you could just uncheck, or unset them.  it doesn't work, however, since karmic.  i'm using lucid, and it still doesn't work.  

[this]("http://ubuntuforums.org/showthread.php?t=1305081") thread shows a not very elegant workaround that's worth a try.

---

### Post by deserthowler on 2011-08-30
I tried this link for 10.04 

[http://linuxexpresso.wordpress.com/2010/05/09/disable-suspend-and-hibernate-ubuntu/]()

It worked great!!!  I rebooted and they were gone from the login and the shutdown menu!!!!

I'll try this on 11.04 later.

Earl

---

### Post by deserthowler on 2011-08-31
Worked on 11.04 too 

Earl

---

