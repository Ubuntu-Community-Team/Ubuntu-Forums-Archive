---
title: "Get rid of IM icon"
date: 2011-04-09
forum: General Help
---

### Post by eric489 on 2011-04-09
Hi all !


I've recently uninstalled the IM client which can with my ubuntu-based distro installation.

But the problem is that the icon is still shown on the bar.

Any advice for how I can get rid of it ?

I've already restarted my computer.

Here's a screenshot : 

[[img]http://s3.noelshack.com/uploads/images/17038094360166_capture.png[/img]](http://s3.noelshack.com/upload/17038094360166_capture.png)

Thanks in advance.

---

### Post by hansdown on 2011-04-09
Hi eric489.

Try right clicking it, and select 

```
remove from panel
```

---

### Post by Enigmapond on 2011-04-09
That is actually part of the Indicator applet session which also includes the button next to it for shutting down. Right click on it and remove from panel.

---

### Post by eric489 on 2011-04-09
> **Enigmapond said:**
> That is actually part of the Indicator applet session which also includes the button next to it for shutting down. Right click on it and remove from panel.

Doesn't work, I just get the details of the menu bar

[http://s3.noelshack.com/upload/8330121464544_capture1.png](http://s3.noelshack.com/upload/8330121464544_capture1.png)

---

### Post by Enigmapond on 2011-04-09
Looks like you locked down the panel icons. I'm not sure how to unlock them...I know Ubuntu-tweak has an option but other than that, I don't know...once you unlock the icons, right-clicking them will give you option to move/remove, etc....

---

### Post by ajgreeny on 2011-04-09
```
sudo apt-get remove indicator-messages
```should do the trick.  It certainly removes the part of the applet for evolution emails and i think also includes IM indicators.

---

