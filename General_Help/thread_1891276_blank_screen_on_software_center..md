---
title: "blank screen on software center."
date: 2011-12-05
forum: General Help
---

### Post by cwparker006 on 2011-12-05
When I open software center, it is just a grey box.  There is nothing except the window control buttons.

I did apt-get update and still get the same results.  


If I got through the terminal and open it, I get this error.

[COLOR="Red"]2011-12-05 09:11:01,436 - softwarecenter.ui.gtk3.em - INFO - EM's: 16 14 18
2011-12-05 09:11:02,375 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file[/COLOR]


I can open it through the terminal if I use sudo software-center.

Is there anyway to correct this?

---

### Post by lechien73 on 2011-12-05
Hi & welcome to the forums,

You could try moving the cached software centre data. The fact that it works with sudo indicates that it could be an issue with your profile.

```
mv ~/.cache/software-center ~/
```

This will move the software-center directory to your home folder. Please then try running the software center again. If it works, then you can delete the software-center directory from your home folder.

---

### Post by cwparker006 on 2011-12-05
Thank you for your help.  That worked great.

---

### Post by lechien73 on 2011-12-05
Cool...you're welcome. I'm glad it helped :D

---

