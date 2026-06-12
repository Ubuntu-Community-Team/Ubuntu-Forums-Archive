---
title: "Permissions are (seriously) messed up"
date: 2009-08-01
forum: General Help
---

### Post by NikolaiKalashnikov on 2009-08-01
Recently my linux installation has been messing up really bad,

It started when every time I booted up,my panel icons would be shifted around,and some even missing.
It won't allow me to run programs with root privileges,even though I'm a sudo-er,it doesn't even ask me for the administrative password,it just doesn't allow me to perform actions which require root access,such as hard drive partitioning,formatting,programme installation.And because of the panel icons getting randomly removed I can't even access the internet because I can't select which network to connect toso I'm using the net right now through my XP partition (ugh).
I can't even use the console because it says I'm not a sudo-er or something like that,even though I know I am,I'm the only account on this computer and I know for a fact it's an administrative account.

Is there any way I can reset the permissions to default?

Any help is greatly appreciated!
Thanks,
NiK.

---

### Post by NikolaiKalashnikov on 2009-08-01
bump,please help me with this!

---

### Post by michy99 on 2009-08-01
First, to make sure you haven't somehow removed yourself from the admin group, open a terminal and enter the command```
groups
```If admin isn't listed, then that is the problem.

---

### Post by _khAttAm_ on 2009-08-01
Here you go:
[http://ubuntuforums.org/showthread.php?t=1000600](http://ubuntuforums.org/showthread.php?t=1000600)

---

### Post by SPr on 2009-08-01
What does
```

more /etc/sudoers

```
report?

If you can't gain root priviledge then it's pointless checking the file with visudo
```

visudo -c

```
Beaten to it. I'm a slow typer.

---

