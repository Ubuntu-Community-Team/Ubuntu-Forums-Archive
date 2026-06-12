---
title: "startx not working"
date: 2009-09-06
forum: General Help
---

### Post by c0mput3r_n3rD on 2009-09-06
Hello all,
  My problem is that when I press ctr+alt+F2, it drops to the black screen, but I can't run startx to restart the GUI.  Here is the error message:
```

xauth:  error in locking authority file /home/matthew/.Xauthority
xauth:  error in locking authority file /home/matthew/.Xauthority
xauth:  error in locking authority file /home/matthew/.Xauthority
xauth:  error in locking authority file /home/matthew/.Xauthority
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running
xinit:  Server error.
xauth:  error in locking authority file /home/matthew/.Xauthority

```

Any help would be greatly appreciated.

---

### Post by NoaHall on 2009-09-06
First -
sudo /etc/init.d/gdm stop
Then
sudo startx

---

### Post by falconindy on 2009-09-06
Press ctrl-d or ctrl+alt+f7 to return.

---

### Post by c0mput3r_n3rD on 2009-09-06
> **NoaHall said:**
> First -
sudo /etc/init.d/gdm stop
Then
sudo startx

Thanks noahall, the only problem is that now my panel wont load properly.  Any ideas on a fix for that?

---

### Post by NoaHall on 2009-09-07
try "killall gnome-panel" and then if it doesn't come back, "gnome-panel"

---

