---
title: "Nvidia update"
date: 2006-05-05
forum: General Help
---

### Post by gos1 on 2006-05-05
I got an error message while trying to run quake3 arena 
---------
Error: GLimp_Init() - could not load OpenGL subsystem
---------
I searched this forum and found out that I have to upgrade my drivers (nvidia) But I dont know how to do that can anyone help me ?

---

### Post by sYs^ on 2006-05-05
Did you install your driver by the nvidia installer?

---

### Post by gos1 on 2006-05-05
i really dontknow but.I followed the instructions at ubuntuguide.org

---

### Post by sYs^ on 2006-05-05
type this to a terminal: *cat /etc/X11/xorg.conf | grep -i glx *
and tell me the output, I think you won't have to update your driver, but I'm not sure. :>

---

### Post by sYs^ on 2006-05-05
If you really want to update your driver here's the best method:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2)

---

### Post by gos1 on 2006-05-05
here is my output tahnks a lot for your help.
---------
 Load    "glx"
--------
I also dont know to upgrade any of the packages like firefox, totem, etc. Where can I find documents about this softwars updates...

---

### Post by sYs^ on 2006-05-05
Well, then I hope the updating will help

---

### Post by tseliot on 2006-05-05
[QUOTE=gos1]I got an error message while trying to run quake3 arena 
---------
Error: GLimp_Init() - could not load OpenGL subsystem
---------
I searched this forum and found out that I have to upgrade my drivers (nvidia) But I dont know how to do that can anyone help me ?[/QUOTE]
The updates of the xserver messed up the OpenGL.

You need to reinstall the driver.

---

