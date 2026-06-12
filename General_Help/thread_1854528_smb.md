---
title: "smb://"
date: 2011-10-04
forum: General Help
---

### Post by Aydos on 2011-10-04
Hello All,

I have not used Ubuntu in a while and I have it running on one of my laptops at work now. 

Everything is Mircosoft here and I have always been able to use my Linux laptop fine. Never had a problem adding it to active directory or accessing anything I need.

However, with my recent install of Ubuntu 11.10 ( I believe it did this on 11.04 as well, but I do not remember) I am not able to access shares the same way.

I can go to the home folder > file > connect to server and do everything that way, but in 10.04. and 10.10 I use to be able to hit alt + f2 and then type smb://hutchfs/st for example to get the the st folder on our hutch fs server. Now, when I type the command the run windows closes and nothing happens.

Does anyone have any ideas on how to resolved this?

I believe it is something different in unity from the old gnome  desktops, but I am not sure.

Thank you in advance.

---

### Post by mcduck on 2011-10-04
Were you really able to do that in the *run dialog* in the previous versions? That's strange, as it definitely wouldn't count as an executable command... Typing that into the location field of the file manager would make sense but run dialog sounds rather weird.

Anyway, the run dialog on classic Gnome desktop is a feature of gnome-panel, while Unity has it's own dialog for the purpose. So it's the same keyboard shortcut, but different program.

---

### Post by Aydos on 2011-10-04
> **mcduck said:**
> Were you really able to do that in the *run dialog* in the previous versions? That's strange, as it definitely wouldn't count as an executable command... Typing that into the location field of the file manager would make sense but run dialog sounds rather weird.

Anyway, the run dialog on classic Gnome desktop is a feature of gnome-panel, while Unity has it's own dialog for the purpose. So it's the same keyboard shortcut, but different program.

Ahh, that must be why. Yeah I am sure I just did it lol. I just cant do it in Gnome Shell or Unity for some reason. It still works in KDE.

---

### Post by Aydos on 2011-10-06
Well I can find many posts and bug reports like the one below, but no work around.

[https://bugs.launchpad.net/unity-lens-applications/+bug/770126](https://bugs.launchpad.net/unity-lens-applications/+bug/770126)

---

### Post by mcduck on 2011-10-06
> **Aydos said:**
> Well I can find many posts and bug reports like the one below, but no work around.

[https://bugs.launchpad.net/unity-lens-applications/+bug/770126](https://bugs.launchpad.net/unity-lens-applications/+bug/770126)

Like that bug report's status tells, it's not a bug, since Unity is a different program than what people have used to do that in the past, and isn't even supposed to handle such things (URL is not a command). The bug report is confirmed, but marked as "wishlist" meaning that the idea is good and might be implemented in the future.

For now you'll probably just have to open the file manager, hit Ctrl-L to show the location bar and enter the URL there instead.

---

### Post by Morbius1 on 2011-10-06
And what happens when you:

alt + f2
```
 nautilus smb://hutchfs/st
```

Same problem?

---

