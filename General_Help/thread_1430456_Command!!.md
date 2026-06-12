---
title: "Command!!"
date: 2010-03-15
forum: General Help
---

### Post by harivittal.hk on 2010-03-15
"sudo /etc/init.d/gdm restart"

Wots the work of this command, will it restart ur entire system??

Pl let me know about this.

Thanks.

---

### Post by nerdy_kid on 2010-03-15
it will restart your login manager (gdm) which will cause all running apps to close instantly.
it will not cause your whole pc to reboot, however.

---

### Post by kio_http on 2010-03-15
No it will just restart the login manager. (The welcome screen component of ubuntu that lets you login in your user)

---

### Post by llawwehttam on 2010-03-15
You could also use ```
sudo service gdm stop
``` in ubuntu.

It will do the same thing which is to restart the login manager. I use this if Installing graphics drivers etc....

---

### Post by harivittal.hk on 2010-03-15
Thank all...:)

---

### Post by harivittal.hk on 2010-03-15
guys Y it's  "init.d" ie am asking about tat .d extension...

---

### Post by llawwehttam on 2010-03-15
There are millions of strange extentions in Linux, for instance you can use a .bak or .backup extention on a folder and all sorts.

Someone else may be able to explain it better.

Also please try to refrain from using txt language as your posts are harder to read.

---

### Post by n0dix on 2010-03-15
> **harivittal.hk said:**
> guys Y it's  "init.d" ie am asking about tat .d extension...

Maybe the '.d' if for daemons. Only guessing.

---

### Post by mikemelen on 2010-03-15
#man init.d 

for more info.

The  scripts  for  controlling the system are placed in ***/etc/init.d/*** (they have been moved according to the Linux
Standard Base (LSB) specification).  These scripts are executed directly or indirectly by **/sbin/init**, the  father
of all processes. The configuration of **/sbin/init** is given by the file **/etc/inittab** (see [inittab(5)]("http://man-wiki.net/index.php/5:inittab")).

---

