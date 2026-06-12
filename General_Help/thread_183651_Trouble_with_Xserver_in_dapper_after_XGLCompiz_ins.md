---
title: "Trouble with Xserver in dapper after XGL/Compiz installation"
date: 2006-05-28
forum: General Help
---

### Post by lemix on 2006-05-28
i read the XGL/Compiz installation guide here....

[http://www.ubuntuforums.org/showthread.php?t=131253](http://www.ubuntuforums.org/showthread.php?t=131253)

and did the first post, but now my Xserver screen wont boot up with either ATI display drivers or FGLRX or Anything else.

My specs to my computer are in my signature. Other than that information i dont know what information to provide you with because i am recently new to linux.

Im running Dapper Drake 6.06 Beta

---

### Post by lemix on 2006-05-28
Wow... ???
The Xserver just crashed on boot but when i got out of it my Desktop was there!
Im in but the Xserver is very unstable.

I altered my GDM.conf file from the post
[http://www.ubuntuforums.org/showthread.php?t=131253](http://www.ubuntuforums.org/showthread.php?t=131253)
but then i changed it back to get this to work.

Very weird...
fglrxinfo output:
> [QUOTE]
lemix@lemix:~$ fglrxinfo
display :0.0 screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20040924 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
[/QUOTE]

It has never displayed Tungsten Graphics as the Vendor String for me...???

Please help any way you can. All help is very much appreciated.

---

### Post by lemix on 2006-05-28
Some how when i reloaded the Desktop after the Xserver Crashed the last know good configuration came up Xgl/Compiz didnt work, Compiz ouputs No Composite Extension.

---

