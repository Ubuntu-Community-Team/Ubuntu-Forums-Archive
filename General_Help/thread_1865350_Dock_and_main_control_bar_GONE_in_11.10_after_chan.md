---
title: "Dock and main control bar GONE in 11.10 after changing dock settings in compiz"
date: 2011-10-20
forum: General Help
---

### Post by andrewcd on 2011-10-20
Hi All,

I'd appreciate your help with a weird problem.  I downloaded compiz in order to change to dock settings to "never hide."  After I did so, I somehow got stuck in a very odd state.  

--The dock is gone
--The normal menu bar (with power status, shutdown, clock, etc) is gone.
----In its place is the menu bar for a file borwser window -- File, Edit, View, Go, Bookmarks, Help
--The Super Key DOES NOT WORK to show the dock
--Alt-F2 DOES NOT WORK to get commands

This is really bizarre.  I am stuck in a file browser (which works, and I can open my files), with no way to get to a terminal (besides control-alt-f2) and no way to get to any applications except those associated with my files.  I feel like I should be abe to right-click the menu-bar at the top and tell it to minimize, but its not right-clickable.

I really appreciate any help!

EDIT:  The keyboard shortcut to get to the terminal works -- control-alt-t

EDIT2:  Some things that don't work:
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset

---

### Post by belzeblubb on 2011-11-15
Hi

Have you checked "Ubuntu Unity Plugin" in CompizConfig?

---

### Post by andrewcd on 2011-11-15
> **belzeblubb said:**
> Hi

Have you checked "Ubuntu Unity Plugin" in CompizConfig?

what I did was go running back to Ubuntu 10 and away from Unity, which I tried oh so hard to be open-minded about, before coming to the conclusion that it was trash design with bugs to boot.

---

