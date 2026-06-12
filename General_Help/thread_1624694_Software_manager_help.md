---
title: "Software manager help"
date: 2010-11-18
forum: General Help
---

### Post by bazerka on 2010-11-18
Ok so i have 2 questions, First when i try installing some apps from the software manager i get :
Dependency is not satisfiable: libqt4-network (>= 4:4.5.3) 
what does this mean and how do i fix it? o.o

secondly for some of the applications they require different sources (universe, main etc.) but when i try installing these sources it tells me to put in the maverick meerkat cd rom, i dl the virtual cd and i have the .iso can i use that for the source? and if i can how do i do it? is there a virtual drive program i can use? Thanks
-Baz

---

### Post by sikander3786 on 2010-11-18
For the first one, please post the output of

```
sudo apt-get update
```

```
sudo apt-get install -f
```

For the second one, go to Software Center > Edit > Software Sources > Other Software Tab and disable the CD-ROM.

---

