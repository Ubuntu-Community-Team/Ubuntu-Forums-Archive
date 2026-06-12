---
title: "No such interface `org.gnome.evolution.dataserver.Calendar'"
date: 2011-11-03
forum: General Help
---

### Post by jokop on 2011-11-03
hello from an old newbie
I'm using ubuntu 11.10 hebrew version.
I'm trying to save a new task/meeting in a in evolution calendar but unable to save.

it messages:

"No such interface `org.gnome.evolution.dataserver.Calendar' on object at path /org/gnome/evolution/dataserver/Calendar/1847/702"

---

### Post by jpborjas on 2011-12-02
Same message here...

---

### Post by bi9kahuna on 2011-12-05
I've run into the same error on both a machine that was upgraded from 11.04, and a fresh install of 11.10.  This is affecting not only my Google calendar (created as a Google calendar as as a CalDAV calendar too, just in case), but also my local "Personal" calendar.

I'll post back here if I figure out how to get this going.  Hopefully somebody else already has!

---

### Post by jwood1961 on 2012-01-24
I experience the same error trying to add an event to my google calendar in Ubuntu 11.10, Unity (all updates applied). Invitation arrives by email; open email, searches calendars for conflicts according to preference settings, and indicates if there is a conflict in a particular calendar. So far so good. Select calendar you want to add to, then press "Accept" - first time - nothing happens apparently; second time, then information message appears "Unable to add to calendar [x]. No such interface 'org.gnome.evolution.dataserver.Calendar' on object at path /org/gnome/evolution/dataserver/Calendar/xxxx/xx'.

JW

---

### Post by fussl on 2012-02-03
I have the same problem!!
Has anyone found a solution oder a work-arround?

---

### Post by ivanp on 2012-02-22
Same problem here

---

### Post by herensuge on 2012-04-13
I solved it as follow:

rm -r $HOME/.config/evolution/calendar

When you execute evolution again, it create the folder and u can create new events (I suppose old are loss...).

Regards

---

### Post by dcstar on 2012-04-13
> **herensuge said:**
> I solved it as follow:

rm -r $HOME/.config/evolution/calendar

When you execute evolution again, it create the folder and u can create new events (I suppose old are loss...).

Regards

Evolution changed the structure and location of its database files in the Ubuntu 11.10 release, it is possible that the conversion on some systems did not run correctly and creating a fresh folder via this method fixes that.

You should actually rename the existing ~.config/evolution folder and then manually copy items from it into the new one.

---

