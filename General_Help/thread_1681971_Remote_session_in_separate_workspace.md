---
title: "Remote session in separate workspace"
date: 2011-02-05
forum: General Help
---

### Post by satjat on 2011-02-05
Hello,

I am heavily using remote X11 via ssh (from Ubuntu to Ubuntu).
The method I am using is connecting with ssh -X and then running the X application I want to use.
Most of the times this is adequate but some times I need to have a desktop view. Running gnome-session in the ssh session, produces a couple of errors (printer and other hardware related) which appears normal but at the end it works. 
The problem is that desktops end up mixed up with windows from all sessions together and the panels and menus from the last session.

What I am trying to achieve is to have each gnome session in a specific workspace. It will be easy using shortcuts like ctrl-super-right/left to move between different machines. Can something like that be achieved?
I know the easy solution would be to vnc to all machines and maximize the vnc viewer in the desired workspace, but this would be really slow and against the linux way of thinking (as is trying to get the remote gnome desktop, but that is another story).
Another solution would be to open the gnome panels in a titled window, so that I can see them all at once and distribute them across workspaces. But how do I do that?

---

### Post by Habitual on 2011-02-05
[Devilspie]("http://foosel.org/linux/devilspie")

---

### Post by satjat on 2011-02-06
Very good.
Still, how would it detect the gnome panels of the remote session?
The application_name would still be "gnome_session".
Also, aren't panels duplicated on all workspaces by default?

---

