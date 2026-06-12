---
title: "Trouble with &quot;Find&quot; Tool in Dolphin File Manager"
date: 2012-04-01
forum: General Help
---

### Post by Iggy64 on 2012-04-01
I am running Ubuntu 11.10 with the LXDE Desktop Environment.  After trying various file managers, I find that Dolphin fits all my criteria.  I have one problem with it though: I do not know how to make the "Find" tool work.  When I want to find a file, I run Find, and it opens up a dialog box above the right panel, into which I type my search term.  As soon as I start typing, the status bar at the bottom of the panel announces "Invalid protocol."  I have no idea what that means, and I could not find an informative answer in the on-line user guide for Dolphin.

Perhaps I am missing some dependencies from KDE?

Does anyone know what that error message means?  Can you suggest how I can make this Find tool run in Ubuntu (LXDE)?

---

### Post by SBKch on 2012-04-20
Same problem here. Does realy noone know how to solve this?

---

### Post by paoos on 2012-05-30
I have solved this by installing kde-baseapps package:

> sudo apt-get install kde-baseapps

---

### Post by JBA2337 on 2012-10-30
> **paoos said:**
> I have solved this by installing kde-baseapps package:

I also had the same problem. I installed kdebase-apps, restarted Dolphin.
Did not help. Every time I type anything after Find: I get the "Invalid protocol" message, and it does not find anything.

Any other ideas how to fix this?


JBA2337

---

### Post by Iggy64 on 2012-11-28
Now, 7 months later, I opened Dolphin again and tried a search, just for kicks.  Guess what?  The search tool runs just fine now.  I don't have any idea why.  I'm still running LXDE on Ubuntu.  The only difference is that it is Ubuntu 12 instead of 11.  

Whatever, Dolphin now suits all my needs as a file manager: Tree view in left pane, details view, and search tool.  Too bad it required dragging in a bunch of dependencies.

If you are one of the other posters who had problems with Dolphin's search early in the year (see thread above), try it again if you are on Ubuntu 12.  Maybe it will work now?

---

### Post by indyend on 2013-07-18
I'm in this situation. Hope it's can use without do anything ^_^...

---

