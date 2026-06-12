---
title: "my ubuntu was bit by a puppy and lost its video"
date: 2009-10-18
forum: General Help
---

### Post by rubing on 2009-10-18
I installed the newest ubuntu the other day, which works fine!  However, after that I installed Puppy linux which saves some files on the ubuntu partition and unfortunately broke the video after doing so.  

Now, when using ubuntu it drops me to terminal for login and x will not work.  I updated and upgraded, but that didn't fix it.  I also tried the recovery mode xfix, which did not work.  


When I 'startx'  I get the following errors:

exec: 5: /usr/bin/X11/X: not found
giving up.

xinit:  No such file or directory (errno 2):  unable to connect to X server

xinit:  No such process (errno 3):  Server error.

Even more interesting when I 'exec gdm'  I recieve the following and then am dropped BACK INTO A LOGIN PROMPT!!

gdm[3857]: WARNING: GDM file gdm-daemon-config.c: line 2042 (): Cannot run seteuid to 0: Operation not permitted
GDM file gdm-daemon-config.c: line 2042 (): Cannot run seteuid to 0: Operation not permitted

Puppy Linux
Linux 2.6.3.05 [i686 arch]

---

### Post by mike555 on 2009-10-18
start on a live cd and go into your installed ubuntu and delete the saved puppy files...... next time install puppy to it's own partition


although I can't understand why puppy files would hurt ubuntu.

---

