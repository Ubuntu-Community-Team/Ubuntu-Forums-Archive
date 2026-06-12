---
title: "dockbarx install problem"
date: 2010-08-20
forum: General Help
---

### Post by fooey on 2010-08-20
I'm trying to install DockBarX for gnome-panel, but I'm getting some dependency errors, which can normally be easily resolved.

[http://i.imgur.com/YzAA3.png](http://i.imgur.com/YzAA3.png)

On my home box, i have the exact same setup as I do here at work. Same version (10.04.1) & same repositories. At home it's working fine.

[B]I must have enabled some "latest greatest" repo at one point in time here on my work box. So it must have upgraded a few of those important dependencies to newer unsupported versions that dockbarx's dependencies rely on. 
[/B]A couple that i notice, which are newer versions than what i have on my home box, are cpp-4.4(4.4.4-5) & gcc4-4-base (4.4.4-5). 
on home rig, i have older versions: cpp-4.4(4.4.3-4ubuntu5) & gcc-4.4-base (4.4.3-4ubuntu5).

now, as i've made sure i have no repos on my work rig to use those latest greatest anymore, is there any easy way to install older versions of those 2 packages and/or remove those 2 & reinstall with what's in my current ppa's (that have versions that dockbarx need). *If I try to remove gcc-4.4-base, it wants to remove every other package i have to make gnome work properly + a ton of my apps i have installed.*

[COLOR="Gray"]so i think it'll come down to this:[/COLOR] i can find gcc-4.4-base (4.4.3-4ubuntu5) (the version that i need), but i have to find a way to overwrite the newer gcc-4.4-base package i have installed on my work machine. any suggestions? can you force install of an older package like that w/o jacking stuff up?

---

