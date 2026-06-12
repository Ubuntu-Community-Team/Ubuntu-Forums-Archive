---
title: "please explain how to start x"
date: 2009-09-27
forum: General Help
---

### Post by Azyl on 2009-09-27
my problem is that every time when i install ubuntu on some computers and need to enter the cd live version of ubuntu it cannot initialize display drivers and reverts to a command line how can i start x so i can run some application like firefox
 
i`ed tryed "sudo startx " and i get an error saying displays found but no config error

---

### Post by SuperSonic4 on 2009-09-27
Can youpost the ouput of 

```
lspci | grep VGA
```

---

### Post by Azyl on 2009-09-27
01:00.0 VGA compatible controller: ATI Technologies Inc Device 9552

i have dell 1525 with ati radeon mobile hd4330 witch it camed with ubuntu but for some app for school i need xp and i want ot resize my partition and i tryed using the live cd to use gparted but it doesnt work and with parted from the command line i`m unsure how it works i use print then resise # and he ask me the start and end ? there is the part that i dont understant and it doesnt say anithing about the partion and the data on the partition so i ill try the gui method

---

