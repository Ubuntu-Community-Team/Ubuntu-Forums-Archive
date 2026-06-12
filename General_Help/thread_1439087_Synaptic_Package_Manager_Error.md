---
title: "Synaptic Package Manager Error"
date: 2010-03-25
forum: General Help
---

### Post by kit294 on 2010-03-25
When I open Synaptic Package Manager I get this Error messege...I tried rebooting but still am unable to open the package manager. Any help would be great. Thanks

[IMG]http://www.wfgraphics.com/pb/images/Screenshot.png[/IMG]

---

### Post by Dantevus on 2010-03-25
I'm sure this is a stupid question for me to ask but stranger things have happened.

Have you opened the terminal and ran the command it told you to run?

---

### Post by michy99 on 2010-03-25
Do what it says. Open a terminal and enter```
sudo dpkg --configure -a
```

---

### Post by doas777 on 2010-03-25
howdy,
 you will prolly want to open a terminal, from Applications -> Accessories -> Terminal, and enter this command:
```
sudo dpkg --configure -a
```
oh, and be sure to close synaptic before you run the command.
hth

---

### Post by kit294 on 2010-03-25
I tried it a second time after rebooting and it worked! Many Thanks!!

---

