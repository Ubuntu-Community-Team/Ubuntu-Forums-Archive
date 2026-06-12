---
title: "How to install pidgin screen let ?"
date: 2009-08-27
forum: General Help
---

### Post by brijith on 2009-08-27
Hai,

I got the the source from [http://gnome-look.org]("http://gnome-look.org/content/show.php?content=72611&forumpage=9"). But when I run it by entering to the extracted directory I got the following error. 

```
Desktop/Pidgin$ python PidginScreenlet.py 
CachingBackend: Loading instances from cache
Found a running session of Pidgin, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Pidgin was not provided by any .service files
Screenlet has already been added to /tmp/screenlets/screenlets.brijith.running
Loading instances in: /home/brijith/.config/Screenlets/Pidgin/default/
No instance(s) found in session-path, creating new one.
/home/brijith/.config/Screenlets/Pidgin/default/Pidgin1
LOAD NEW THEME: default
FOUND: None
Found Pidgin..
Traceback (most recent call last):
  File "PidginScreenlet.py", line 1522, in <module>
    screenlets.session.create_session(PidginScreenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 472, in create_session
    session.start()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 254, in start
    sl.finish_loading()
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 1243, in finish_loading
    self.on_init()
  File "PidginScreenlet.py", line 1391, in on_init
    self.refreshBuddyList()
  File "PidginScreenlet.py", line 1422, in refreshBuddyList
    self.getGroupsAndBuddies()
  File "PidginScreenlet.py", line 205, in getGroupsAndBuddies
    self.addBuddy(buddyId)
  File "PidginScreenlet.py", line 232, in addBuddy
    self.addBuddyAndGroup(buddyId, groupId, groupName)
  File "PidginScreenlet.py", line 269, in addBuddyAndGroup
    self.setBuddyIconImage(buddy_obj, self.layout.buddy_icon.size)
AttributeError: 'NoneType' object has no attribute 'buddy_icon'

```

Another doubts is how to get this screenlet listed in the ubuntus screenlet application.....


[COLOR="DarkRed"]**Thanks**[/COLOR]

---

### Post by brijith on 2009-08-27
Friends,

I got it. I had to copy the extracted folder to ~/.screenlets/. once I copied it it worked !....



:)

---

