---
title: "Package dependencies cannot be resolved"
date: 2011-04-07
forum: General Help
---

### Post by Sylore on 2011-04-07
Hello. basically,I'm in a computer engineering class. For our classes computers, we installed ubuntu(close vote, i voted for windows).
 
Anyway, as I was installing Java, my computer got shut off and now I have the following problem as I try to install anything from the software center:
 
Package dependencies cannot be resolved.
 
 
I cannot download any of the software required and re-installing is a last resort. I turn to you guys for help, as nothing any of us have done has worked.
 
 
I'm having a terrible with this OS, hopefully you guys can change that. Thanks!

---

### Post by oldos2er on 2011-04-07
Open a terminal (Applications, Accessories, Terminal), and run ```
sudo dpkg --configure -a
```

---

### Post by Krytarik on 2011-04-07
Run these commands in a terminal and post the outputs of those, in code-tags please, the #-button in the editor:
```
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get upgrade
```

---

