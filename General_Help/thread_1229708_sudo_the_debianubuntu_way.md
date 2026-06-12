---
title: "sudo the debian/ubuntu way"
date: 2009-08-02
forum: General Help
---

### Post by nikhilbhardwaj on 2009-08-02
one thing i specially like about ubuntu and debian is that after you enter the password running a command with sudo
you dont have to enter it again for some time and can run more commands

this is very convinient
but in other distro's this isn't the case
you either have to enter the password for each command you run 
which is very frustrating
or change to nopasswd all in /etc/sudoers
which is unsecure 

i've managed to buld my own Linux from Scratch system reading the subversion book 
i want to implement sudo the way ubuntu/debian do 

what are the steps to achieve this

---

### Post by cariboo on 2009-08-02
You will probably have to compile sudo and it's dependencies in order to get it to work. OF course you could always run as a normal user and use su to change to root to do what you need, the press Ctrl-d to exit.

---

### Post by ridetheteapot on 2009-08-02
in /etc/sudoers
Defaults:ALL timestamp_timeout=<time_in_minutes>
if you set this for a long time and want to kill the timestamps manuelly when your finished 'sudo -K'

---

### Post by nikhilbhardwaj on 2009-08-02
> **ridetheteapot said:**
> in /etc/sudoers
Defaults:ALL timestamp_timeout=<time_in_minutes>


thanks a lot
that did the trick

---

