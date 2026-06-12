---
title: "GIMP will not start"
date: 2012-01-15
forum: General Help
---

### Post by solitario on 2012-01-15
Hi folks.
The GIMP will not start. The cursor spins a bit and then nothing. I've tried restarting, installing/re-installing through the software center. Nothing.
Any help is appreciated. Thanks.

---

### Post by Q-collective on 2012-01-15
> **solitario said:**
> Hi folks.
The GIMP will not start. The cursor spins a bit and then nothing. I've tried restarting, installing/re-installing through the software center. Nothing.
Any help is appreciated. Thanks.

Could you create a test user to see if Gimp works there? This way we can determine if the issue is user-related or systemwide.

You can create a new account via the System Settings > User Accounts menu.

If you're more comfortable with a terminal, you could also start Gimp in a terminal and see what the output is.

---

### Post by solitario on 2012-01-18
hi there.
nope. creating a new user does not work. the only way i can start gimp is by doing sudo gimp. Like this:

kyle@kyle-Inspiron-531:~$ sudo gimp
[sudo] password for kyle: 
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:9198): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/helpbrowser: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

(gimp:9198): LibGimpBase-WARNING **: gimp: wire_read(): error

===============
p.s. now that i've created a new user, my windows have this "roll up" effect when maximize, etc. i think i can figure that one out.
thanks.

---

### Post by WorMzy on 2012-01-18
Don't run graphical applications with sudo, you might do more damage to your home area that way. Use gksudo (or equivalent) if you need to run an application as root.

I suggest that you uninstall the local version you've installed (presumably through make install), and install the officially supported version from the repositories.

```
sudo apt-get install gimp
```

You may need to fix the ownership of, or remove, the ~/.gimp-2.6 from your home folder before the application will run. The repo version that is, the current version apparently won't run without a library that Ubuntu doesn't provide.

---

### Post by solitario on 2012-01-19
thanks WorMzy. no dice. think i'll just do a whole upgrade. thanks.

---

