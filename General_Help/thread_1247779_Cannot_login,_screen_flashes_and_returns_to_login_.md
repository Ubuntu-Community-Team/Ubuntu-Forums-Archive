---
title: "Cannot login, screen flashes and returns to login screen"
date: 2009-08-23
forum: General Help
---

### Post by matt_lethargic on 2009-08-23
Hi linux nearly noob here!

Have been working on and off with linux for some years now, but I've never really had any bad issues to fix and don't even know where to start.

Basically I shut the server down to move and now that its back up I can't login, I'm using 8.14 (I think, ran distro update a few weeks ago.... or something) started life as 8.10. Every time I try login in weather its via login prompt (Ctrl Alt F1) or via the usual GNOME login screen it thinks for a second and then goes back to the login screen.

I think its something to do with the authentication service as I cannot login via ftp and samba doesn't seem to allow me in either.

Basically HELP!! I need to get loads of stuff off it fast!

Thanks in advance. and let me know if I have to provide any more info... not that I can get into the mahcine!!!

---

### Post by kambrik on 2009-08-23
Try booting with a live cd and then try to fix the services.

---

### Post by matt_lethargic on 2009-08-23
How to i go about fixing the services?
Any commands or links welcome :)

---

### Post by mkoop on 2009-11-18
I've got the same issue. When logging in with the correct password, after some screen flashes, it returns to the login screen again. Any idea what to do?

---

### Post by Rinzwind on 2009-11-18
Could you check the file 
.xsession-errors
in your home dir for errors?

---

