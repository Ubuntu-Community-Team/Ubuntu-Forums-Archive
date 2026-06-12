---
title: "Amarok Problems"
date: 2006-04-18
forum: General Help
---

### Post by short4lif2 on 2006-04-18
I have had Amaarok installed for a long time and it has worked flawlessly, making it my favorite media player for linux, but lately, a  problem arose.  When I switched from ubuntu to kubuntu using apt-get (apt-get install kubuntu-desktop)  i never got around to deleting gnome.  When I finally did, everything went smoothyl except for one thing.  The deletion of evolution has made Amarok screw up.  When I start the problem from the panel, the application closes, and starts thunderbird with an email that says 

> amaroK has crashed! We're terribly sorry about this :(

But, all is not lost! You could potentially help us fix the crash. amaroK has attached a backtrace that describes the crash, so just click send, or if you have time, write a brief description of how the crash happened first.

Many thanks.

Engine: gst-engine
Build date: Oct 4 2005
CC version: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
KDElibs: 3.4.2
TagLib: 1.3.1
NDEBUG: true

since reading the attachment would be too complicated, I ran Amarok in the terminal and got the following output.
```

$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
kio (Scheduler): FATAL: BUG! _ScheduleJob(): No extraJobData for job!

```

---

### Post by uteck on 2006-04-18
I think the sound engine got removed.  Try installing amarok-arts, amarok-engines, amarok-gstreamer, and amarok-xine just to make sure you have a viable engine to use.

---

### Post by short4lif2 on 2006-04-18
yeah it didn't work

---

### Post by trotski on 2006-04-18
You may want to try renaming or removing the folder:

~/.kde/share/apps/amarok/

---

### Post by short4lif2 on 2006-04-18
You're the winner trotski, thankyou very much for your help

---

