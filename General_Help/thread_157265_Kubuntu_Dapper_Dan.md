---
title: "Kubuntu Dapper Dan"
date: 2006-04-08
forum: General Help
---

### Post by Red Knuckles on 2006-04-08
Where can I get the latest version of Kubuntu Dapper Dan? Can I upgrade a Breezy Badger install to latest Dapper Dan?:)

---

### Post by trotski on 2006-04-08
O Brother, Whereart Thou...

Dapper Drake can be found here:
[http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-6/](http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-6/)

---

### Post by aysiu on 2006-04-08
[QUOTE=Red Knuckles]Can I upgrade a Breezy Badger install to latest Dapper Dan?:)[/QUOTE] Dapper Drake? Sure. Copy and paste these commands into the terminal (KMenu > System > Konsole): ```
cd /etc/apt
sudo -s
mv sources.list sources.list_breezy
sed 's/breezy/dapper/g' sources.list_breezy >sources.list
apt-get update
exit
sudo apt-get dist-upgrade
```

---

