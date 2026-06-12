---
title: "Getting command to stick in config file"
date: 2009-11-10
forum: General Help
---

### Post by kestrel1 on 2009-11-10
Possibly easy, but I can't figure it out yet. I am trying to get Cairo-Dock to work under Xubuntu 9.10. Not a problem, I hear you cry. Well for a bit more info look at this thread:
[http://ubuntuforums.org/showthread.php?t=1315794](http://ubuntuforums.org/showthread.php?t=1315794)
Basicaly the part I am stuck on is, how can I get a command to stay as I want it & not change at logout in the ~/.cache/sessions/xfce4-session-***
file.
I have the following line that reads:
```
Legacy0_Command=cairo-dock
```
& I want it to read:
```
Legacy0_Command=cairo-dock -c
```
so that Cairo-Dock will start without asking me if I want to run it with OpenGL support.
If I change the file & restart/ logoff & log back in the changes have reverted to the original command without my changes & I get the OpenGL question again.
How can I change the sessions file & get it to keep the changes after a reboot etc. Automatically save sessions is not ticked, so it shouldn't be saving the session.
Any ideas?

---

### Post by kestrel1 on 2009-11-10
BUMP.
Anyone?

---

### Post by alphaniner on 2009-11-10
I don't use xfce so I can't confirm, but have you looked into the 'xfce4-session.rc' file?

---

### Post by kestrel1 on 2009-11-10
> **alphaniner said:**
> I don't use xfce so I can't confirm, but have you looked into the 'xfce4-session.rc' file?
Looked for the file, but it cannot be found on the system. From what I could tell it should be in the xfce4-session folder, but it isn't. Before long I will scrap Xubuntu in favour of Ubuntu, although I do like the xfce desktop. I have Ubuntu & Xubuntu on the same machine, so I might keep it for a while.
Any other thoughts on this welcome.
Cheers

---

