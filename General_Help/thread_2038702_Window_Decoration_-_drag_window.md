---
title: "Window Decoration - drag window"
date: 2012-08-07
forum: General Help
---

### Post by kurci2 on 2012-08-07
Hi!
I am using Kubuntu 12.04; KDE installed 4.9 via repos.

I have a problem (it was present also in KDE 4.8) with dragging windows around the sceen if i change Window Decoratin theme.
The problem is that if i change theme then drag is delayed.
So, i grab a window (for example VLC or any other) and move mouse already over half of my sceen and only now the window moves.

But if i leave default theme everything works perfectly.
It is not really a big problem, but it is annoying.
Does anyone know what is the issue?

---

### Post by samigina on 2012-08-08
Its a know bug. Are you using Aurorae? Take a loke [here]("http://blog.martin-graesslin.com/blog/2012/08/fixing-slow-window-movment-in-4-9/") for more info and a workaround.

---

### Post by kurci2 on 2012-08-09
that's great man!
Thank you very very much.
I have been looking for this solution for a long time.

I'll just post this tolution here as well =)
```

cd /tmp
wget https://projects.kde.org/projects/kde/kde-workspace/repository/revisions/9ee6a775d592ec3f105892c32c7576d6cdd7c210/diff/kwin/clients/aurorae/src/qml/aurorae.qml?format=diff
cd /usr/share/kde4/apps/kwin/aurorae/
sudo patch -p6 -i /tmp/aurorae.qml\?format\=diff

```
than:
```
Alt+F2 (Krunner)
kwin --replace
```
Source: [http://blog.martin-graesslin.com/blog/2012/08/fixing-slow-window-movment-in-4-9/](http://blog.martin-graesslin.com/blog/2012/08/fixing-slow-window-movment-in-4-9/)

---

