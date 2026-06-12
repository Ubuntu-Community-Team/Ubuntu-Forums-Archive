---
title: "cannot find cod installation directory:("
date: 2009-09-24
forum: General Help
---

### Post by BAMF1501 on 2009-09-24
OK i installed cod 4 went to find my director activision in wine c: folder but its not there and i pressed ctrl-h to refresh still not there i even rebooted also and still doesnt have no trace of activision folder ;(

---

### Post by gismo93 on 2009-09-24
are u sure it will say activision?

ive never installed cod4 on pc but maybe try looking for a directory along the lines of infinity ward or call of duty or something?

---

### Post by BAMF1501 on 2009-09-24
there is no folder iin that nature ugh!! i cannot find it :(

---

### Post by BAMF1501 on 2009-09-24
bump

---

### Post by credobyte on 2009-09-24
```
find ~/.wine -name activision

```

Still nothing ?

---

### Post by BAMF1501 on 2009-09-24
i typed 
find ~/.wine -name activision in terminal and still no work

---

### Post by BAMF1501 on 2009-09-24
bump

---

### Post by j.bell730 on 2009-09-24
Find is case sensitive...
```
find ~/.wine -name Activision
```
Otherwise, perhaps
```
find ~/.wine -name Infinity*
find ~/.wine -name Call*
```

---

### Post by BAMF1501 on 2009-09-24
NOn work :(

---

### Post by j.bell730 on 2009-09-24
I once had an application that installed to "Application Data". Run these commands and search through the directories.
```
nautilus ~/.wine/drive_c/windows/profiles/*/Local\ Settings/Application\ Data
nautilus ~/.wine/drive_c/windows/profiles/*/Local\ Settings/Application\ Data
nautilus ~/.wine/drive_c/windows/profiles/*/Application\ Data
```

---

### Post by BAMF1501 on 2009-09-24
sill cant find :(

---

### Post by BAMF1501 on 2009-09-25
bump

---

### Post by BAMF1501 on 2009-09-25
bbuummpp

---

### Post by BAMF1501 on 2009-09-25
can someone please help :(

---

### Post by BAMF1501 on 2009-09-26
ok now its wierd i installed far cry and the directory for that doest show up :(

---

### Post by shuffman37 on 2009-09-26
If I were you open us Disk usage analyzer, scan your home folder and look for the games files. It'll probably eat up about 4gb or so of space so it should be really easy to find that way. Then just navigate to the folder its located in.

---

### Post by BAMF1501 on 2009-09-26
i found it thanks to ^^ it was in my playon linux directory cause thats what program i used to install it :)

---

### Post by shuffman37 on 2009-10-10
> **BAMF1501 said:**
> i found it thanks to ^^ it was in my playon linux directory cause thats what program i used to install it :)
No problem ;)

---

