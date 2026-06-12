---
title: "LAMP confusion"
date: 2010-11-22
forum: General Help
---

### Post by sean14916 on 2010-11-22
I thought I would play around with php for a while and so set forth to configure apache. Whilst I was reading a website for installing LAMP stuff on ubuntu I thought I would give it a go. I installed a LAMP server with:

sudo tasksel install lamp-server

and lo and behold it crashed my operating system upon restart. So both my laptop and desktop were toast.  Everything is reinstalled now so is fine and I have installed apache2 and php5 from separate packages. The one thing that's troubling me is why it crashed. It seemed to uninstall vlc media player, m-player and gnome-player as well as removing the "switch accounts" button on the lock screen.

Does anyone know 1) why it died and/or 2) why it chose to eliminate those programs specifically.

---

### Post by WorMzy on 2010-11-22
I've seen reports of "tasksel *remove*" having that kind of effect, but never "tasksel *install*". I was under the impression that it'd been fixed, but apparently not. You might want to add your say to the bug report here: [https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/150252](https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/150252)

Until the devs fix it, I'd stay away from tasksel.

---

