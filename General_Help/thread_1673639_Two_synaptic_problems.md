---
title: "Two synaptic problems"
date: 2011-01-22
forum: General Help
---

### Post by ridetheteapot on 2011-01-22
1. When you lock a package shouldn't updates be ignored? I locked a few but the update-manager keeps bothering me about them.

2. Seems like randomly the checkbox for treat recommended packages as dependencies turns true. It has seemed that way for at least a year.

---

### Post by ajgreeny on 2011-01-22
You can do a better job at pinning a package version by editing the /etc/apt/preferences file

To pin a package version add these lines to  /etc/apt/preferences:
```
Package: <name>
Pin: <version> (number from repos)    
Pin-Priority: 1001
```

I can not give you an answer to your other query, as I have never bothered to stop recommended packages being seen as dependencies.

---

### Post by ridetheteapot on 2011-01-22
ok thanks, im running into a problem though...
its the same version as the repos have, just recompiled with different cflags - i saw the 'origin' option for Pin: but i do not know what to use as the origin. I will try with 'origin local', if that doesnt work i'm just going to recompile with version+1 and avoid it all.

----EDIT----
ok just tried that and it didnt work, i think im just gonna recompile

---

### Post by ridetheteapot on 2011-02-09
had already marked as solved, because i thought that pin would not work anyway for my situation (repo version and mine had same version number) and i had planned on just making a new package with a higher version.
If anyone stumbles upon this, don't take pin advice (there is so much you can use pin for, but hold works better for this).
Use HOLD, you can use hold by dropping all the dpkg selections to a text file (dpkg get-selections > file) and edit the entry for your package in the txt from install to hold, and then using dpkg -set-selections to read the modified txt back in. Alternatively aptitude will take the hold command, making it the simplest way i saw, but i think ubuntu no longer installs aptitude by default.

---

