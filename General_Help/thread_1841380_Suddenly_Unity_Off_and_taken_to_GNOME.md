---
title: "Suddenly Unity Off and taken to GNOME"
date: 2011-09-09
forum: General Help
---

### Post by Ronalddig on 2011-09-09
Hello

I have been using 11.04 for moths with no problem. Today when i booted I am taken to GNOME environment rather than Unity.

I dont understand this . What could be the problem ? 

My Gfx driver is working fine . 

pls help

Thanks in advance

---

### Post by howefield on 2011-09-09
Check the session menu at the login screen, have you changed it to Ubuntu Classic in error ?

---

### Post by mmsmc on 2011-09-09
when you boot up, at the login screen look at the bottom of the screen, you should see boot up options(which ubuntu you would like to boot, user defined session, etc), which one is selected?

---

### Post by Ronalddig on 2011-09-09
i have selected ubuntu only ( not the classic one ) . this normally drops me to unity but not now

---

### Post by Ronalddig on 2011-09-10
anyone pls help ??

---

### Post by lahirukannangara on 2011-09-10
try "unity --replace" on terminal :)

---

### Post by raja.genupula on 2011-09-10
```
unity --reset 
```

or 
type ccsm in terminal , in that window just check is that ubuntu unity box marked or not .

---

### Post by Ronalddig on 2011-09-10
i get this when i type **unity -- replace **

> unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: No valid GL extensions string found.
Compiz (bailer) - Info: Ensuring a shell for your session
ankur@ankur-Lap:~$ Cannot register the panel shell: there is already one running


On typing **unity --reset** i get this :

> WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: No valid GL extensions string found.
Compiz (bailer) - Info: Ensuring a shell for your session
ankur@ankur-Lap:~$ Cannot register the panel shell: there is already one running


What do i do next

Thx in advance

---

### Post by linuxuser12345 on 2011-09-10
Are you in the classic mode with no effects?

---

### Post by Ronalddig on 2011-09-10
> **linuxuser12345 said:**
> Are you in the classic mode with no effects?


yes, i am in classic mode and no effects like wobbly windows

---

### Post by raja.genupula on 2011-09-10
move to  Ubuntu with unity session and then try again

---

### Post by Ronalddig on 2011-09-11
Im am in unity session only ( at startup ) yet I am shown gnome2 . thats what the problem is

---

### Post by Krytarik on 2011-09-11
Try following this guide, especially the checking part:

[http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

Greetings.

EDIT: As I'm going to leave now, see this current thread for further hints:
[http://ubuntuforums.org/showthread.php?t=1842210](http://ubuntuforums.org/showthread.php?t=1842210)

---

### Post by VinDSL on 2011-09-11
I had the same problem (for 2 days) - was driving me crazy.

This fixed it:

```

sudo apt-get install ubuntu-desktop

```

Might give it a try...  ;)

---

### Post by Ronalddig on 2011-09-14
Nothing above mentioned worked.

Hence , it just clicked to me to reinstall my nVidia driver for gfx card and everything is working fine now :)

---

