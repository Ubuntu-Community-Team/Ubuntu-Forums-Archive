---
title: "admin mode blues"
date: 2006-02-22
forum: General Help
---

### Post by Derktoon on 2006-02-22
i was attempting to configure my PCMCIA network card on my laptop. So it tells me that i must enter administration mode in order to make changes. makes sence right? anyway, i click the button and a read outline now encircles the window im working in...but nothing shows up in the window. then a few seconds later the red box dissapears and i am aparently out of admin mode. w...t...f

so my wonderings are if there is a way to get into andmin mode and configure my network card via the command line? :-k

---

### Post by Jucato on 2006-02-22
I think it's a bug in KDE 3.4.x. If you can, upgrade to KDE 3.5.1 for best results. 
If you can't upgrade, you can also try to enter  this in a terminal:
```
kdesu kcontrol
```
But this is only a workaround and you would have to do this everytime you try to access a KControl module with administrator privileges.

---

### Post by Derktoon on 2006-02-23
yeah i tried the kdesu and it works to enable the NIC for about 15 seconds...but ill try and get the upgrade, where could i DL that from?

---

