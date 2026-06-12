---
title: "removing unecessary programs"
date: 2009-11-16
forum: General Help
---

### Post by honey toast on 2009-11-16
can i delete palm OS devices from my 9.10 wireless laptop without any repercussions? 
can I remove 'mousetweaks' too? They both have a whole bunch of dependencies. I don't use a mouse on my laptop. I use the touch pad.

---

### Post by phillw on 2009-11-16
> **honey toast said:**
> can i delete palm OS devices from my 9.10 wireless laptop without any repercussions? 
can I remove 'mousetweaks' too? They both have a whole bunch of dependencies. I don't use a mouse on my laptop. I use the touch pad.

Are you short of disk space ?
Is your system broken ?

No ? -- leave it alone :D

JMHO

Phill.

---

### Post by oldos2er on 2009-11-16
> **honey toast said:**
> can i delete palm OS devices from my 9.10 wireless laptop without any repercussions? 
can I remove 'mousetweaks' too? They both have a whole bunch of dependencies. I don't use a mouse on my laptop. I use the touch pad.

 Yes. If you're like me, and you know you'll never be hooking up a PDA to your computer, or using mouse accessibility enhancements, run ```
sudo aptitude remove gnome-pilot gnome-pilot-conduits mousetweaks
```

 Here's the output in case you're interested (I ran two separate 'remove' commands):

sudo aptitude remove gnome-pilot gnome-pilot-conduits
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  gnome-pilot gnome-pilot-conduits 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4,088kB will be freed.
Writing extended state information... Done
(Reading database ... 314086 files and directories currently installed.)
Removing gnome-pilot-conduits ...
Removing gnome-pilot ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

and

sudo aptitude remove mousetweaks                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  mousetweaks 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4,465kB will be freed.
Writing extended state information... Done
(Reading database ... 313994 files and directories currently installed.)
Removing mousetweaks ...
Processing triggers for man-db ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

 There are other packages I routinely remove after an upgrade or fresh install; bluez, evolution, tracker, and one or two others I can't remember right now. Never has caused a problem.

---

