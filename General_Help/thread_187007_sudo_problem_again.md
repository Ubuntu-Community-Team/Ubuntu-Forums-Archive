---
title: "sudo problem again"
date: 2006-06-02
forum: General Help
---

### Post by saax on 2006-06-02
I have a problem using sudo aptitude ,when i try to install something like VLC
i get this>

ueulo@ubuntu:~$ sudo aptitude install vlc
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "vlc"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

 I think i need to update system im new to KDE so can someone tell me where to go and how to update.I already post similar thread ,but i was using ubuntu gnome and it was diferent.

PLease,help

---

### Post by denjin on 2006-06-02
[quote=saax]I have a problem using sudo aptitude ,when i try to install something like VLC
i get this>

ueulo@ubuntu:~$ sudo aptitude install vlc
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "vlc"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

 I think i need to update system im new to KDE so can someone tell me where to go and how to update.I already post similar thread ,but i was using ubuntu gnome and it was diferent.

PLease,help[/quote]
You have all the extra repositories un commented in your /etc/apt/sources.lst file, right?  vlc is in the universe one.

---

