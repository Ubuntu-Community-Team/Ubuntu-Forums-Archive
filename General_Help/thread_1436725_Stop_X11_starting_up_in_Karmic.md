---
title: "Stop X11 starting up in Karmic"
date: 2010-03-23
forum: General Help
---

### Post by covert on 2010-03-23
I have a Ubuntu desktop install I would like to stop X11 from starting up on bootup. I want to do this to try to set up stand alone xbmc and Mythtv without X running since it is a low spec machine. (appleTV)

Is it just a rc file I need to edit ?

---

### Post by thebigob on 2010-03-23
Not 100% sure on this one however if you are looking to set up a headless server (ie a pc with no monitor required) then I would use Ubuntu server edition as this comes with the minimal installed. This means it is faster and you only run what you put on it. This also means that X would not start unless you install it.

If this is not suitable then you could try removing the x11 packages but as I have not done this I would wait for someone more in the know to post before trying this approach.

---

### Post by darolu on 2010-03-23
Ubuntu reaches runlevel 2 by default, I'm not sure if making it to reach runlevel 1 only will prevent X from starting up but you can try, simple delete (or move) the corresponding rc files at /etc/, rc0.d = run level 1, rc1.d = runlevel1, rc2.d = runlevel2 and so on, so you would need to delete/move all rc#.d but rc0.d and rc1.d.

More info in these links: 

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

---

### Post by john newbuntu on 2010-03-23
In Karmic, the upstart is used to kick off jobs.  Move the file /etc/init/gdm.conf (and probably kdm.conf) out of the way.  Just save it someplace else.  Then reboot.  If you encounter any problems, restore these files.
"service gdm stop" from a virtual terminal also does the trick.

---

