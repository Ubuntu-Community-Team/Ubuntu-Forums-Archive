---
title: "X11 Forwarding Not Working"
date: 2009-08-19
forum: General Help
---

### Post by zzzBrett on 2009-08-19
X11 Forwarding is turned on the sshd config, but I am getting the following error after connecting using putty with X11 Forwarding enabled (client side) to localhost:0


```

user@server:~$ gedit
(gedit:16416): Gtk-WARNING **: cannot open display: localhost:10.0

```



What does this error mean?

---

### Post by zzzBrett on 2009-08-20
bump

---

### Post by geirha on 2009-08-20
You need to run an Xserver on the client. One of the first hits on google was this: [http://www.math.umn.edu/systems_guide/putty_xwin32.html](http://www.math.umn.edu/systems_guide/putty_xwin32.html)

---

### Post by zzzBrett on 2009-08-20
Both my client and server are running ubuntu.  I thought I already had an X server running on the client..

---

### Post by mjwalfredo on 2009-08-20
Why are you using putty then?  You can just use the ssh client and specify the -X argument.  That should work.

I use it this way "ssh -c arcfour,blowfish-cbc -XC host"

That enables compression for a more responsive session.

---

