---
title: "Help removing folder ~"
date: 2011-03-02
forum: General Help
---

### Post by I3roknI3ottle on 2011-03-02
The OS is Ubuntu Server 10.10 x64, no gui

TLDR

I was trying to define the downloads complete & incomplete folders in sabnzbdplus via the webpage from my laptop.  I was trying to make it my raid / mounted drives and for some reason of messing around in the process put ~/home/adam/downloads & sabnzbdplus created a folder in my home directory called "~" , if I try and remove this folder (rm -r ~) it deletes everything in my home practically (I know I tried it).  Can anyone help me remove this folder?

[http://cl.ly/4vho](http://cl.ly/4vho)

SOLVED - "rm -r /home/adam/~"

Thanks mcduck!

---

### Post by mcduck on 2011-03-02
Instead of trying to do "*rm -r ~*" (which will always point to your home directory) use the full path to the directory you want to remove: "*rm -r /home/adam/~*"

---

### Post by I3roknI3ottle on 2011-03-02
that worked wonderfully, thank you!

lesson definitely learned.

---

