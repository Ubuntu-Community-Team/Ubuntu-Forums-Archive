---
title: "I can see only my wallpaper"
date: 2011-07-02
forum: General Help
---

### Post by Dim360 on 2011-07-02
Well, I was messing up with compiz when I accidently had the status bar of my windows removed.(Minimize etc) Then I rebooted but when I try to log in I can only see my wallpaper, and my mouse cursor. Any help?

---

### Post by hawthornso23 on 2011-07-02
Hit ctrl alt F1 to login to a terminal session. Then 
```
unity --repair
```
or possibly
```
unity --reset
```
(I can never remember which it is), should fix your problem.

---

### Post by Dim360 on 2011-07-02
> **hawthornso23 said:**
> Hit ctrl alt F1 to login to a terminal session. Then 
```
unity --repair
```
or possibly
```
unity --reset
```
(I can never remember which it is), should fix your problem.

Then reboot?

---

### Post by Dim360 on 2011-07-02
It worked!!!!! Thank you sir!

---

### Post by hawthornso23 on 2011-07-02
You are welcome. Please mark thread as solved.

Unity in 11.04 breaks easily if you change compiz settings. Compiz works better in the ubuntu classic desktop.

---

### Post by wildmanne39 on 2011-07-03
Hi, also here is a guide to set up compiz with out breaking unity, it is written for the cube and effects.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by Dim360 on 2011-07-03
Thanks both.

---

