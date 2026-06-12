---
title: "Update manager"
date: 2011-11-26
forum: General Help
---

### Post by Brizlitman on 2011-11-26
Update manager says:
Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Type ‘ain’ is not known on line 3 in source list /etc/apt/sources.list.d/myunity-ppa-oneiric.list'

---

### Post by zeroseven0183 on 2011-11-26
Hi! That problem is caused by either a mistakenly edited line on the file, particularly in line 3. Could you post here the results of ```
cat /etc/apt/sources.list.d/myunity-ppa-oneiric.list
```I suppose the word should be 'main' and not 'ain'.

If it's true, then carefully edit the file through Gedit or any text editor you like (Vi, Vim, Nano), save it then run again Update Manager.

---

### Post by Brizlitman on 2011-11-26
deb [http://ppa.launchpad.net/myunity/ppa/ubuntu](http://ppa.launchpad.net/myunity/ppa/ubuntu) oneiric main
deb [http://ppa.launchpad.net/myunity/ppa/ubuntu](http://ppa.launchpad.net/myunity/ppa/ubuntu) oneiric main
ain

---

### Post by zeroseven0183 on 2011-11-26
You can remove than 'ain' in the last line, save the file then run ```
sudo apt-get update
```

---

