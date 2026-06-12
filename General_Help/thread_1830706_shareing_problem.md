---
title: "shareing problem"
date: 2011-08-22
forum: General Help
---

### Post by Rakeshvijayan on 2011-08-22
hi friends 

I am facing problem for sharing a folder located on Desktop 

I right click on the folder and hit on share folder .its download some fiel and installed .but its not shared I need 

this sharing for using vertual box this is my screen shot. how can i recover from this

---

### Post by Morbius1 on 2011-08-22
Make sure you have the following package installed:
```
sudo apt-get install samba-common-bin
```
Then restart samba:
```
sudo service smbd restart
```
OR
```
sudo service smbd start
```

---

### Post by Rakeshvijayan on 2011-11-10
problem happen  again to while I am going to make a new share on my desktop . share option not displayed on the right click on folder what can  I do [samba             samba-common      samba-common-bin ] this where installed my desktop 

expecting your help soon as possible 

Thanks

---

### Post by Morbius1 on 2011-11-11
```
sudo apt-get install nautilus-share
```

---

