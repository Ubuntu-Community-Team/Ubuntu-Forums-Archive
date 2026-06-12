---
title: "Resolution of login screen"
date: 2006-04-24
forum: General Help
---

### Post by jazzgossen on 2006-04-24
How can I change the resolution of the graphical login screen? By default, it seems to use the maximum possible resolution, which is a bit too much for me.

---

### Post by frodon on 2006-04-24
All you need is already here, don't forget the search function of the forum ;) :
[http://www.ubuntuforums.org/showthread.php?t=151192](http://www.ubuntuforums.org/showthread.php?t=151192)
[http://www.ubuntuforums.org/showthread.php?t=124543](http://www.ubuntuforums.org/showthread.php?t=124543)
[http://www.ubuntuforums.org/showthread.php?t=140335](http://www.ubuntuforums.org/showthread.php?t=140335)
[http://www.ubuntuforums.org/showthread.php?t=135994](http://www.ubuntuforums.org/showthread.php?t=135994)

---

### Post by jazzgossen on 2006-05-10
I tried the solutions in those threads (editing xorg.conf so that the desired resolution is listed first). Now, the screen resolution is how I like it (1280x960), but the login image still uses the higher resolution, which means that I can't see the options in the lower part of the screen (Session, System...), for example. 

Where can I change that? And shouldn't the login screen be scaled to whatever resolution is used?

---

### Post by frodon on 2006-05-10
For the login screen resolution have a look to this thread : [http://ubuntuforums.org/showthread.php?t=140335](http://ubuntuforums.org/showthread.php?t=140335)

---

### Post by confused57 on 2006-05-13
Look at the link frodon provided.  I had the same problem, the native resolution of my CRT is 1024 X 768 and the login screen resolution was too high.

You may want to backup your  /etc/X11/xorg.conf  before making changes.

You'll need to: 

  sudo gedit /etc/X11/xorg.conf

Scroll down & you should see  the line  "DefaultDepth  24",
if you do, scroll down to the Depth 24 settings and set the 
native resolution of your monitor as the 1st resolution in the list.
You can see examples in the link from frodon.  I had tried 3 or 4
suggestions before finally finding the correct solution.

Ignore my post, I see you've already tried this.

---

