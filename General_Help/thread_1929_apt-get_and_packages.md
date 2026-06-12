---
title: "apt-get and packages"
date: 2004-10-24
forum: General Help
---

### Post by jayclark on 2004-10-24
Simple questions. When you download something with apt-get/synaptic. Does it just download in a temp directory and delete them after installing or do the packages stay on the hardrive?

---

### Post by water on 2004-10-24
you can choose this in the synaptic preferenses.
 
 :water

---

### Post by Dracontopes on 2004-10-24
I think "apt-get autoclean" does something like this (cleaning packages)

Try "apt-get --help" for additional info.  ;)

---

### Post by Sebastian Richter on 2004-10-24
Hi,

they do stay. And they do this in:

/var/cache/apt/archives

Bye,

Sebastian

---

### Post by FLeiXiuS on 2004-10-24
[QUOTE=Sebastian Richter]Hi,

they do stay. And they do this in:

/var/cache/apt/archives

Bye,

Sebastian[/QUOTE]


apt-get autoclean will solve this problem..

---

### Post by Sebastian Richter on 2004-10-24
I didn't want to say, that thats a problem. ;)

---

