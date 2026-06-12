---
title: "eth0 cannot get online anymore!? Please help."
date: 2006-04-13
forum: General Help
---

### Post by touser on 2006-04-13
Hello everyone i am running ubuntu 5.10 and i have 2 ethernet cards: eth0 and eth1. eth0 connects to my internal lan as well as my dsl modem through a nat router. Eth1 connects only to my cable modem which i use explicitly for my windows 2000 vmware client. Ever sense i installed vmware after about 10 minutes i am unable to ping anything on the internet through eth0, the only way to fix this i have found is to run: "dhclient eth0" and then suddenly i can get back online for about 10 minutes, then i have to do it again. The whole time i am still able to ping my internal network just fine through eth0 though. Does anyone know of a solution to this as typing "dhclient eth0" every 10 minutes isnt going to work... Thanks in advance!

---

### Post by rabidphage on 2006-04-13
[http://ubuntuforums.org/showthread.php?t=158659](http://ubuntuforums.org/showthread.php?t=158659)

try this 
in short try dropping the interface that you don't want

---

### Post by touser on 2006-04-13
Thanks for the reply. Will dropping an interface dissable it? Because if it permanently disables it that isnt an option, i need both interfaces working simultaniously. Thanks!

---

