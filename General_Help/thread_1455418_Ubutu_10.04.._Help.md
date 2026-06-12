---
title: "Ubutu 10.04.. Help"
date: 2010-04-15
forum: General Help
---

### Post by charreedawn on 2010-04-15
I am trying too update to 10.04, it was going just fine but it stops at 51 mins left till done. I took a pic so u can see what it says... I dont want to resat Because it may just not work at all... so how do I fix this?? Plz help:(

 
[IMG]file:///home/charreedawn/Desktop/Screenshot.png[/IMG]

---

### Post by linden940 on 2010-04-15
you may just have to restart...not sure what to tell you

---

### Post by howefield on 2010-04-17
Try the Lucid forum, you might be more likely to get specific help.

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by 3rdalbum on 2010-04-17
If the upgrade is stalled, then there's not really anything else you can do except to quit it.

Before rebooting, try running:

```
sudo dpkg --configure -a
```

If all else fails, then reboot; you may be pleasantly surprised to find that the system comes up and works. Or it doesn't. But Linux's modular nature means that the system is still likely to work to a degree even when part-way between distros.

---

