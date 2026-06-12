---
title: "how to use sudo in a shell script"
date: 2011-04-08
forum: General Help
---

### Post by wxuyec on 2011-04-08
hi, I have a bash script like belows:

wmctrl -a synaptic || sudo synaptic

and I bind a short key S-y to that script.

it used to work well before. but today I 
found it didn't work. the application of 
synaptic didn't start. and if I delete the
sudo thing, the synaptic will start. but
in this case I can't change anything.

---

### Post by wxuyec on 2011-04-08
I found an alternative method.
I binded a key to sudo scriptname.
and add a line in the /etc/sudoers
xxxx ALL=(root) NOPASSWD: scriptname

now it works. but I don't know whether
it will cause other problems.

---

