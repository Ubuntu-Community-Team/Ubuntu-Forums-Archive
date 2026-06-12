---
title: "Can deskbar display Tracker results?"
date: 2011-03-06
forum: General Help
---

### Post by Virgofenix on 2011-03-06
Similar to the way Deskbar can display Beagle results live, can it do the same for Tracker? I hate having to put open the Tracker window every time I have to do a search.

---

### Post by Virgofenix on 2011-03-06
bump

---

### Post by luigi_mb on 2011-03-06
Trecker installs Tracker-Status-Icon on the panel. It looks like a magnifying lense and it flashes in a different color while indexing.


/luigi

---

### Post by Virgofenix on 2011-03-07
Thanks for replying, luigi.

Yes, I am aware of the tracker-status-icon. Unfortunately, it doesn't have a keyboard shortcut unlike deskbar(Alt-F3) and still needs to open the "Tracker Search Tool" window which makes things slow for me.

I remember deskbar being able to show tracker results just like Beagle's in prior versions of Ubuntu. Actually, I think the package was called: libdeskbar-tracker ([google search](http://www.google.com/search?client=ubuntu&channel=fs&q=libdeskbar-tracker&ie=utf-8&oe=utf-8)). They took out this feature in 10.10?

---

### Post by Virgofenix on 2011-03-08
Still open.

---

### Post by in0giro on 2011-03-08
same deal here.  i have seen it work when i first installed the Deskbar handler from [http://svn.gnome.org/svn/tracker/trunk/python/deskbar-handler/tracker-module.py](http://svn.gnome.org/svn/tracker/trunk/python/deskbar-handler/tracker-module.py)
every time after, even upon reinstalling, same deal.

looks like it is at least on the radar:
[https://bugs.launchpad.net/ubuntu/+source/deskbar-applet/+bug/680594](https://bugs.launchpad.net/ubuntu/+source/deskbar-applet/+bug/680594)

---

### Post by Virgofenix on 2011-03-10
in0giro,

I'm trying to install the same module. Where's the folder it's supposed to go into?

---

### Post by in0giro on 2011-03-10
> **Virgofenix said:**
> in0giro,

I'm trying to install the same module. Where's the folder it's supposed to go into?

according to the page here [http://live.gnome.org/DeskbarApplet/Extending](http://live.gnome.org/DeskbarApplet/Extending) one should be able to drag the link to the Python file directly into the Deskbar preferences window.  i can confirm that it installs and shows up as a handler, but it does not actually show live results.  also, not sure if it is the fault of the Tracker live search handler, but Deskbar crashes multiple times a day for me.

peace

---

### Post by macey on 2011-04-30
You had to install libdeskbar-tracker in Lucid. I am currently trying out Natty. Same problems with tracker and Deskbar-applet. Tried to install libdeskbar-tracker. Got message saying package is referred to by another package but not installable.
E: Package 'libdeskbar-tracker' has no installation candidate.

---

### Post by alx96 on 2011-08-07
I can not get this feature to work too. I read somewhere that the deskbar suppose to be able to act as interface for tracker, so you don't have to use the tracker default search dialog.

---

### Post by macey on 2011-08-07
> **alx96 said:**
> I can not get this feature to work too. I read somewhere that the deskbar suppose to be able to act as interface for tracker, so you don't have to use the tracker default search dialog.

Correct

---

### Post by in0giro on 2011-08-07
looking at the new/current Tracker DBus interface

[https://live.gnome.org/Tracker/Documentation/DBusAPI](https://live.gnome.org/Tracker/Documentation/DBusAPI)

it seems like the Deskbar Tracker plugin uses the old Tracker DBus API:

[http://svn.gnome.org/svn/tracker/trunk/python/deskbar-handler/tracker-module.py](http://svn.gnome.org/svn/tracker/trunk/python/deskbar-handler/tracker-module.py)

thus, the Tracker Deskbar handler would have to be updated to use the new SPARQL query syntax, possibly via [http://developer.gnome.org/libtracker-sparql/unstable/](http://developer.gnome.org/libtracker-sparql/unstable/)

until this happens, it looks like the Tracker Deskbar handler will not work.

peace

---

