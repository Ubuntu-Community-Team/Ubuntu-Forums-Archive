---
title: "CompizConfig screwed up everything!"
date: 2011-08-31
forum: General Help
---

### Post by LorteMidget on 2011-08-31
Hi, I Downloaded CompizConfig, to get some 3D effects, but when I picked, which settings I wanted, and pressed "apply", my sidebar, and top bar on the desktop was gone, and I couldn't do anything. If i want to login, I have to choose "Ubuntu Classic" theme.. But I want the new theme with the Sidebar..

When I choosed the options in CompizConfig, I deactivated som plugins, which is the problem (I'm pretty sure). But I can't remember those plugins..

So, what can I do, besides recovering my system to yesterday?

---

### Post by alexy_ on 2011-08-31
try to reset unity in terminal : ```
$ unity --reset
``` 
then logout/login

if not better you can try to reset compiz:
```
$ gconftool-2 --recursive-unset /apps/compiz-1
$ unity --reset
```
logout/login

---

