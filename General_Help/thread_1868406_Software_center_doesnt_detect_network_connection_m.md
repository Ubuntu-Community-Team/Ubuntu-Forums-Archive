---
title: "Software center doesnt detect network connection made through gnome-ppp"
date: 2011-10-24
forum: General Help
---

### Post by kanishkdudeja on 2011-10-24
I use wvdial and gnome-ppp to connect to my reliance net connect data card..

but software center doesnt detect the network connection..

therefore i cannot install anything using software center..

any workarounds to this?

---

### Post by kanishkdudeja on 2011-10-25
bump.

---

### Post by AlexDudko on 2011-10-25
Can you ping external ip's? Can you ping domain names?
Does it work if you use NetworkManager?

---

### Post by kanishkdudeja on 2011-10-25
yes i can ping domain names..

yes it does work if i use the network manager..

---

### Post by AlexDudko on 2011-10-25
May be a bug. But why do you use wvdial and gnome-ppp if NetworkManager works great then?

---

### Post by kanishkdudeja on 2011-10-26
Using network manager, sometimes it works and sometimes it does'nt..

sometimes it just goes on and on and never connects..

so i had to use wvdial and network manager..

---

### Post by bigcam87 on 2011-12-10
I have this same problem. I use software center to look for the actual name of the program and then install it via terminal and apt-get  So if you are looking through software center's games and see supertuxkart  go to terminal and:  sudo apt-get install supertuxkart

---

### Post by kanishkdudeja on 2011-12-10
Yeah i do the same too..

But it would be better in case a lot of dependencies need to be installed first..

software center handles those themself..

---

### Post by cody1233 on 2011-12-10
I have had this same problem and never found a way to fix it, but everything still works on mine.  It's probably just a program bug.  Are all your proxy settings like they should be?

---

### Post by raja.genupula on 2011-12-10
i need the output of 
```
sudo apt-get updtae
```
please give me that to understand your problem .

---

