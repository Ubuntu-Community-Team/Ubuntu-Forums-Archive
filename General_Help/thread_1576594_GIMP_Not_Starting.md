---
title: "GIMP Not Starting"
date: 2010-09-17
forum: General Help
---

### Post by lostprophetpunk on 2010-09-17
I installed GIMP 2.6.8 the other day, it was all working fine. I then realised that there was an updated version of GIMP out.

So I searched through google for guides to help me upgrade. I did that...it successfully did it...but whenever I click on GIMP...it says in the taskbar 'Starting GNU Image Manipulation Program', does nothing then disappears.

I have tried uninstalling and re-installing several times now for the 2.7.1 version of GIMP.

Any ideas on why this is happening?

Thanks in advance.

---

### Post by ronnielsen1 on 2010-09-17
Open up a terminal and type in gimp and display any error messages

---

### Post by WorMzy on 2010-09-17
Definitely do what Ronnielsen said. Also, providing a link to the instructions you used may help us understand what you've done.

---

### Post by lostprophetpunk on 2010-09-17
So I run 'gimp' through terminal...

I get a user installation guide for GIMP 2.2.11, and then this in the terminal...

```
root@Mini-PC:~# gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:3392): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/helpbrowser: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

(gimp:3392): LibGimpBase-WARNING **: gimp: wire_read(): error
```

---

### Post by lostprophetpunk on 2010-09-17
Just an update from terminal...

Got this after randomly closed the application...
```
***MEMORY-ERROR***: gimp[3392]: GSlice: assertion failed: sinfo->n_allocated > 0
gimp: terminated: Aborted

(script-fu:3558): LibGimpBase-WARNING **: script-fu: wire_read(): error
```

---

### Post by WorMzy on 2010-09-17
2.2.11? Are you running Dapper Drake?

Could still use the link to the tutorial you used to upgrade, we can't really give any clear advice until we know exactly what you've done.

---

