---
title: "Can't run GParted"
date: 2011-05-25
forum: General Help
---

### Post by Krepta3000 on 2011-05-25
I'm running the Kubuntu 10.10 live CD, and I can't run GParted.  It keeps asking for a password, which I don't know, since it's a Live CD.  The reason I'm trying to run it is because I've been trying to fix my windows XP disk, and nothing I've tried has worked.  Windows dies with blue screen of death every time, even in safe mode, and all the other tools I've got aren't working, I am going crazy!!  I'll have to reintall windows, yet again, I bet.  I so hate windows!!  But, still need it.

Can you please help?

---

### Post by ankspo71 on 2011-05-25
The live cds already run with elevated privileges so applications shouldn't be asking for a password at all. (it could be being buggy in your case though). 

The username of the live cd should be
username: ubuntu
password: <leave blank>

Since gparted is a GTK application it will be trying to authorize itself with gksudo, but I think it was Kubuntu 10.10 where gksudo didn't like Kubuntu (password was always incorrect) so I had to run applications with kdesudo instead of gksudo. So my suggestion is to try running gparted from the terminal to see if it works (or reports errors). 
Open the terminal (Konsole) and try typing:
```
gparted
```
or
```
kdesudo gparted
```

---

