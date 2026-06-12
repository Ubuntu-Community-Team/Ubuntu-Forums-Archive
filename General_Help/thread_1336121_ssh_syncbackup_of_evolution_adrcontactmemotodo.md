---
title: "ssh sync/backup of evolution adr/contact/memo/todo"
date: 2009-11-24
forum: General Help
---

### Post by n.l.o on 2009-11-24
Hello!

I know this subject has been visited before, but the posts I found were a bit outdated.

Is there any way of syncing/backing up everything except mails in evolution to a server without any special software on the server, i.e. syncML/WebDAV/Cal etc..?

That would be very sweet, since I really only want to rely on my own machines, instead of using ScheduleWorld, Google Calendar/Addressbook etc.

Also doing it over SSH would be even sweeter. I tried looking into Conduit but it doesnt seem to work that well.

Cheers

---

### Post by mo.reina on 2009-11-24
rsync?  it comes with most linux distros

---

### Post by n.l.o on 2009-11-24
yes, but which local folders should be synced?

and aren't they specific for the system, i.e. for that host etc

---

### Post by dcstar on 2009-11-25
> **n.l.o said:**
> yes, but which local folders should be synced?

and aren't they specific for the system, i.e. for that host etc

Look in the .evolution folder and find the ones you want.

---

