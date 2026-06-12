---
title: "Thunderbird broken - Doesn't show any folders"
date: 2010-05-21
forum: General Help
---

### Post by Crusty Juggler on 2010-05-21
Hi all-
I'm pretty sure this is a fairly common issue, as I have had it before, but I can't remember how I fixed it, other than nuking Thunderbird and recovering what I can.

Out of nowhere, when I open Thunderbird it doesn't show any of my folders or messages (see attached photo).  It still has account settings and all that and even appears to be downloading messages, but it doesn't show anything.  The most frustrating thing is that it worked fine yesterday, and is broken today.

When I launch it from the terminal, I get the following error:
```
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [libxul.so: cannot open shared object file: No such file or directory]
```
If I uninstall IcedTea, no more error, but it still doesn't work.  If I run in safe-mode, it doesn't work.  If I manually disable all plug-ins, it still doesn't work.

Can anyone help?

---

### Post by Peter09 on 2010-05-21
Just for a sanity check - there is a menu just above the folders pane which allows you to select which folders to see - unread, recent, favourites etc. Check what that is set to, make sure its 'all'

---

### Post by Crusty Juggler on 2010-05-21
Doesn't matter.  Whichever is chosen, nothing is shown.

---

### Post by albinootje on 2010-05-21
> **Crusty Juggler said:**
> 
Out of nowhere, when I open Thunderbird it doesn't show any of my folders or messages (see attached photo).

Make a backup of .mozilla-thunderbird/ (and/or .thunderbird/) and try this :
[http://ambermcleod.com/blog/?p=24](http://ambermcleod.com/blog/?p=24)

---

### Post by Crusty Juggler on 2010-05-24
Oddly enough, tonight I opened Thunderbird to follow the list from albinootje's link and it magically works fine.  It must have heard me say "Screw it, I'm going to try out Evolution..."

I'll mark it as solved, even though spontaneous fixing doesn't really constitute solving a problem, and to me, is just as frustrating as the problem itself.

---

### Post by Detonate on 2010-05-24
I suspect something happened to your profile data, and it repaired itself when you restarted TB.  You might want to browse your profile and make sure the permissions are all correct, with you as the owner of all of the folders and files in your TB profile.  It could be a permissions problem.

---

### Post by unc0nn3ct3d on 2010-09-28
Alright, a few hours later of mucking about with this file by file I think I've managed to fix it.

It came down to my foldertree file being corrupted(my hard drive is slowly swirling the drain).  Just delete that file, let thunderbird recreate it on the next startup and everything comes back just hunky dory.

Enjoy

---

