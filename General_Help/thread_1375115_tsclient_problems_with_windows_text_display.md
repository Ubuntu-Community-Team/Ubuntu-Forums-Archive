---
title: "tsclient problems with windows text display"
date: 2010-01-07
forum: General Help
---

### Post by tendonstrength on 2010-01-07
Hello,

I am using tsclient to connect to a windows server 2003 machine, and I am having problems with some of the text on the windows machine not displaying. Sometimes it works and sometimes it doesn't. I have tried messing around with the settings for the connection, but changing the resolution and color options doesn't really seem to help.

Attached is a screen capture of the problem. Thanks in advance for any help with this.

---

### Post by tendonstrength on 2010-01-07
I haven't found a solution to the problem with tsclient, but I found out about krdc, which is the KDE remote desktop client. I have installed it and it doesn't seem to have the same problem. It also just seems better all the way around.

---

### Post by tendonstrength on 2010-01-07
Actually after using it a little more, it looks like krdc has this problem as well. Is there some setting I'm missing? I have had this problem with tsclient, rdesktop and now krdc. 

Thanks

---

### Post by tendonstrength on 2010-01-07
After more digging I found out that this had to do with my Nvidia video driver. The solution is pretty simple and can be found here:

[http://ubuntuforums.org/showthread.php?t=3407](http://ubuntuforums.org/showthread.php?t=3407)

---

