---
title: "Window dragging(moving) choppy/laggy"
date: 2012-02-09
forum: General Help
---

### Post by ArmandoPR on 2012-02-09
I recently installed CompizConfig Settings Manager (ccsm) on my ubuntu 11.10 and moving/dragging windows animation is choppy/laggy. I had the propietary nVidia drivers installed.

After a fresh login window dragging is smooth for about a second or then, then it messes up again. I also uninstalled ccsm but the problem was still there, so i installed ccsm again just in case. I have also played with the v-sync options for but still no progress. :(

Any information regarding this issue? Thanks in advanced, Armando.

---

### Post by jasonrisenburg on 2012-02-09
try unity --reset
it might help

---

### Post by stinkeye on 2012-02-10
Have had this bug all through 11.10 using nvidia or nouveau drivers.
Still exists in my 12.04 testing install.

---

### Post by chiefmanyrabbitguteat on 2012-02-25
I got significant improvement when I did the following:

Install compiz-config settings manager and load it

Click on "Window Decration"

Change the entry in "Command" from
```
/usr/bin/compiz-decorator
```
to
```
/usr/bin/unity-window-decorator
```

That worked for me.

---

### Post by stinkeye on 2012-02-25
Still the same.
If I open a new window and grab the titlebar and move it works smoothly.
But if I release and then attempt to move again it is jerky.

---

### Post by noobermin on 2012-12-16
Did you ever figure this out? I'm having the same issue, although I didn't install anything. This started after a full screen gaming session.

---

