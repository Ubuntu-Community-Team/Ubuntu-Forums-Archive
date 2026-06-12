---
title: "Ubuntu 10.04 startup script"
date: 2010-09-17
forum: General Help
---

### Post by A.Zan on 2010-09-17
Ok nothing special but i finally got this working so i'm going to post here how i made it

Let's suppose you need to add this to a startup script so the  VNC4server starts automatically when booting:   vnc4server :1


You need to: 

1- Create a new file named "vnc-startup.sh", and write your command inside it ( vnc4server :1 ..... )
2- Put it in /etc/init.d/ directory
3- Make it executable: sudo chmod +x vnc-startup.sh
4- Let it come with startup: update-rc.d vnc-startup.sh defaults

This should make it start with boot up.

.

---

