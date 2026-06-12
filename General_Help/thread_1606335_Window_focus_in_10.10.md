---
title: "Window focus in 10.10"
date: 2010-10-26
forum: General Help
---

### Post by venik212 on 2010-10-26
I am using Ubuntu 10.10 (64 bit).  When I want to focus on a window, I used to be able to click anywhere in the window and get its attention, but now (since 10.10) I must click on the title bar-- clicking in the window area does not do it.
I tried the "Raise selected windows after an interval", but I do not like this behavior.
Thanks for any help--

---

### Post by lavinog on 2010-10-26
That sounds like a bug, and not by design.

Are you using desktop effects? If so, does it occur when you disable them?

Did you update to 10.10, or is this a fresh install?

---

### Post by venik212 on 2010-10-28
--I disabled the desktop effects, but it did not cure the problem.
--I upgraded from 10.04 to 10.10 (not a fresh install)

IT IS TERRIBLE, and I cannot believe that it is happening ONLY to me!

---

### Post by utnubuuser on 2011-10-16
I've got the same prob at the moment, and don't much like it.  Did you find a solution?

---

### Post by utnubuuser on 2011-10-16
Nevermind....


Fix= Alt+F2, type in: gconf-editor, scroll to apps >> metacity >> general >> put a check beside: raise_on_click

---

