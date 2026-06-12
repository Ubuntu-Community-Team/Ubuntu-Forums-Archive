---
title: "Can't find program in Add/Remove or SPM"
date: 2009-08-18
forum: General Help
---

### Post by gregapan on 2009-08-18
I want to uninstall Picasa 3.0. It is not in either the add/remove OR in the Synaptic Package Manager. I can't find it anywhere. (By the way, I was using it, so I know it is installed! :)) 

In addition to helping me locate and kill this particular program, if anyone has wisdom about why this situation occurred, it would be helpful. Uninstalling something ought not to be so difficult, sheesh.

---

### Post by oldos2er on 2009-08-18
How did you install it? Have you tried ```
sudo dpkg -r picasa
``` ?

---

### Post by gregapan on 2009-08-18
Thanks. 
that worked, but again, I would like to know why such a maneuver became necessary. That's not the "official" way, even though it may be nifty. No such code for uninstallation is given by the Help, for example. 

What determines whether a program appears in Add/Remove? It can't be random.

Why was it not in SPM?

Anyone?

---

### Post by michy99 on 2009-08-18
My guess is that you downloaded a .deb file from somewhere and installed it manually.

---

### Post by gregapan on 2009-08-18
Okay, so help me to understand this.
I downloaded picasa from Google's site, using firefox. I double clicked to open the file, ubuntu opens its install window, I click install, and hey presto. After that it's in the graphics submenu of Applications.

Is this what you mean by "manually installed"? 

Should I do it differently? Like using the ubuntu repository?

Still confused by this. Please advise. 
Thanks.

---

### Post by oldos2er on 2009-08-19
dpkg is just as "official" as apt-get, aptitude, Add/Remove, or Synaptic; the only difference is it will operate on *deb files you download yourself, as opposed to *debs from a repository. I suppose that's what is meant by installing "manually".

---

### Post by sg7791 on 2009-08-19
Add/Remove does not work the same way that it does in Windows. On Windows, Add/Remove displays all installed software on the machine. On Ubuntu, Add/Remove and SPM display all software and packages installed as well as uninstalled, but only if they can be found in the installed repositories.

---

