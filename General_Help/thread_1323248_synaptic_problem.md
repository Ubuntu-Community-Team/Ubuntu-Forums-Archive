---
title: "synaptic problem"
date: 2009-11-11
forum: General Help
---

### Post by Jeffonfire on 2009-11-11
Somehow synaptic is jamed. I tried to uninstall ubuntu-ce-sounds but I got this error message "E: ubuntu-ce-sounds: subprocess installed post-removal script returned error exit status 255" now i cant unmark it and it wont let me install anything else.

I need help!

---

### Post by jbrown96 on 2009-11-11
In a terminal (apps-->accessories-->terminal) run the following commands ```
sudo dpkg-reconfigure -a
``` ```
sudo apt-get -f install
``` If you get errors, post them here.

---

### Post by hwttdz on 2009-11-11
From the command line try
sudo apt-get update
sudo apt-get install ubuntu-ce-sounds
sudo apt-get remove ubuntu-ce-sounds
This should give the errors that the removal script ran into.  If you can do it clean you should be able to run synaptic again.  

You can also try
dpkg --configure -a

---

