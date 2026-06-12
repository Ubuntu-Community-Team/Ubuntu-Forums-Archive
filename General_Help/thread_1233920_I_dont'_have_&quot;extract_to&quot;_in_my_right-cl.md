---
title: "I dont' have &quot;extract to&quot; in my right-click menu. New minimal install..."
date: 2009-08-07
forum: General Help
---

### Post by brjoon1021 on 2009-08-07
Hi,

I decided to install Jaunty via a minimal install and start from scratch. Well, I figured out this great thing called file-roller. But, I still don't have any "extract" command in the right-click menu to deal with a .tar or two that I have to work with.

Can you help ?


Also, any ideas of a few really basic needs that I won't have covered (like this one) due to the fact that I made a minimal install ? I don't mean web browser or things like that, but more like file-roller and whatever will fix this issue....

Thanks,

B

---

### Post by shihkster1015 on 2009-08-07
what do you mean by minimal installation?

---

### Post by brjoon1021 on 2009-08-07
Here's the link.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

very bare installation, then you follow this, for example:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)   
however, I went with Gnome-core rather than a window manager.

---

### Post by shihkster1015 on 2009-08-07
why dont you go for the full installation?

---

### Post by snek on 2009-08-07
Try installing file-roller:
sudo aptitude install file-roller

You will probably need to add some more tools like tar unrar and unzip, so:
sudo aptitude install file-roller tar unrar unzip

Hope this solves your problem, not sure if it will add it to the right click menu automatically though.

---

### Post by brjoon1021 on 2009-08-07
thanks.

---

### Post by snek on 2009-08-10
Did this solve your problem? If so rename the thread with [SOLVED] :)

---

