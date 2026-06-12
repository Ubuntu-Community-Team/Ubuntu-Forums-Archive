---
title: "No tray icons for some apps in Kubuntu"
date: 2011-06-29
forum: General Help
---

### Post by Tilex on 2011-06-29
Hi !

I noticed that some applications, like Amarok and KTorrent, do not get minimized in the tray when I close them.

They don't shutdown either, they just disappear from the taskbar and do not show up in the tray icon space.

If I execute "amarok" in the terminal, it says "Amarok is already running!" and then executes.

It's weird because Thunderbird and Virtualbox both show up as tray icons when I launch them.

Any suggestions as to what might cause this on 11.04 ?

Thanks !

---

### Post by Tilex on 2011-07-08
I found the solution to my problem here :
[http://ubuntuforums.org/showthread.php?t=1748145](http://ubuntuforums.org/showthread.php?t=1748145)

I edited the line 
ShowApplicationStatus=false
to
ShowApplicationStatus=true

Hope that helps somebody!

---

