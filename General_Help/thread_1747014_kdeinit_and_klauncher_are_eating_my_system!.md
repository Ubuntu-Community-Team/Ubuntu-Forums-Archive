---
title: "kdeinit and klauncher are eating my system!"
date: 2011-05-02
forum: General Help
---

### Post by Objekt on 2011-05-02
Recently my Ubuntu 10.04 LTS install has seemed sluggish...and I think I know why.

Right after startup, before I launch anything manually, System Monitor shows several dozen instances each of kdeinit and klauncher (listed as "klauncher [kdeinit] --new-startup).  They're constantly shifting, so I can't select and kill them all in the GUI.  They seem to be constantly changing ID numbers as well, so I don't know how I would kill them from the command line either.

What the heck is going on here?  I don't know how this happened.  I don't even use the K Desktop Environment, only straight-up Gnome or Gnome/Openbox.

These processes are keeping both CPUs between 70%-90% busy at all times, so it's amazing I am able to do anything else.

update:
Also remembered that when I go to shut down/restart the system, I'm told there's an "unknown" process running and asked if I want to kill it so I can restart/shut down.  This may be the fleeting unlabeled process that shows up in System Monitor.  I'll try to get some screenshots so I can show what I'm talking about.

update2:
Seems to have something to do with using GNOME/Openbox option at login.  I logged in with plain old GNOME and I don't have zillions of KDEinit processes, or constant CPU hogging.  Weird.

---

