---
title: "Strange Error..."
date: 2006-05-09
forum: General Help
---

### Post by Echo35 on 2006-05-09
A few programs I've tried running end up exiting abnormally with an odd error:

Creating link /home/echo35/.kde/socket-ubuntu.
can't create mcop directory

It's usually the same error with a few programs. So far, this has happened with Neverwinter Nights, and Wine Configuration. Does anyone know what the problem is?

---

### Post by Dantrag on 2006-05-25
Bump this. I am getting the same error. Anyone have any idea?

---

### Post by Echo35 on 2006-05-25
Well, I have made some progress. The error went away completely. However, whenever I hit the "Sound" tab in winecfg, it crashes with this error. Then, after that, my other programs also crash with the error, but only after I got it in winecfg first. Also, when I restart my computer, it goes away untill I open winecfg again, so it seems to be linked to Wine.

---

### Post by groggyboy on 2006-05-25
For me, the solution was surprisingly simple.  In a terminal:> 
modprobe snd-seq
sudo mkdir -p ~/.kde/socket-<hostname>

The first command makes sure that wine has access to a nescessary module.
The second command makes the directory that wine can't find.  Replace <hostname> with the name of your computer.  For Echo35, this would be "ubuntu" (no quotes).

Someone else had posted this fix.  I forget where I found it, but thanks!
Hope this helps.
groggyboy

---

### Post by Echo35 on 2006-05-25
mkdir: cannot create directory `/home/echo35/.kde/socket-ubuntu': File exists

Ok??

---

### Post by groggyboy on 2006-05-26
run winecfg in a terminal, and click on the audio tab.  what's the error say?

---

### Post by Echo35 on 2006-05-26
Creating link /home/echo35/.kde/socket-ubuntu.
 can't create mcop directory

Then a few other programs also get this error. Things like Neverwinter Nights and sometimes Second Life. They don't get it normally, just after I run winecfg. I am doing a fresh install later today of Dapper Drake, so maybe it'll go away?

Note: I do NOT use Kde, so I don't even understand this message at all!

---

### Post by groggyboy on 2006-05-26
Yah, I don't use KDE either (except for amaroK).  Strange...

A fresh install *may* fix it.

Also, try pointing nautilus at /home/<USERNAME>/.kde/socket-ubuntu - is it a folder or a file?  Also, make sure the owner is set to your username, and that everyone has read permissions.  Don't know if this'll help, but let me know!

groggyboy

---

