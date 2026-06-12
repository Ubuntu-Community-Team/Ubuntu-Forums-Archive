---
title: "How To Make .exe open using XFCE desktop?"
date: 2010-06-25
forum: General Help
---

### Post by note32 on 2010-06-25
i seriously can't figure this out in xfce right clicking and selecting it to make it execu. doesn't work and i used the command line and still can't get it to work?:confused:

---

### Post by zaphod777 on 2010-06-25
you need to install wine.

```
sudo apt-get install wine
```

you can check app compatibility here.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

with that said windows apps don't generally run too well on Linux. It is always best to find an app in the app center that will do what you need to do. 

If you must use a certain windows app then you need to use wine.

there is a pay commercial version that has support and generaly works better with Windows apps.

[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by note32 on 2010-06-25
no its not that i have wine installed the application won't open saying 

The file '/home/zach/Downloads/Setup_MakeMKV_v1.5.6_beta_win.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by zaphod777 on 2010-06-25
oh ok check this post it looks like there are multiple solutions to getting the exe to open correctly with Wine.

[http://stream-recorder.com/forum/blocked-wine-start-unix-problem-opening-exe-t6560.html?](http://stream-recorder.com/forum/blocked-wine-start-unix-problem-opening-exe-t6560.html?)

---

### Post by note32 on 2010-06-25
thank you sir solution #3 did the trick thanks):P

---

