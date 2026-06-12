---
title: "tell synaptic to not upgrade a package"
date: 2006-06-23
forum: General Help
---

### Post by joshrobinson on 2006-06-23
how can i tell synaptic not to upgrade something? everytime there is an update for it it annoys me and i dont wana upgrade my compiz because i have it compiled with patches, and the normal installs dont work

can i lock the version somehow?

---

### Post by Ramses de Norre on 2006-06-23
Select the package, click the package menu and choose "lock version" ;)

---

### Post by aysiu on 2006-06-23
Click on the package and then go to Package > Lock Version.

---

### Post by joshrobinson on 2006-06-23
ah thanks guys.. i knew it was in there somewhere.. ive heard of people doing it.. i was just right clicking it and looking in there

thanks again

---

### Post by amanita on 2006-11-12
Hi, when attempt to lock package (package -> lock version) Synaptic suddenly closes. Please help

---

### Post by Ramses de Norre on 2006-11-12
Try these:

1) Just reinstall it, that helps sometimes.

2) Run synaptic from terminal and look at the error output when it closes.

---

### Post by amanita on 2006-11-12
I Run it from terminal and when atempted to lock verison got this output:
[HTML]
(synaptic:10508): Gtk-CRITICAL **: gtk_tree_model_get_iter: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(synaptic:10508): Gtk-CRITICAL **: gtk_tree_model_get: assertion `GTK_IS_TREE_MODEL (tree_model)' failed
Segmentation fault (core dumped)[/HTML]

---

### Post by Ramses de Norre on 2006-11-12
```
Segmentation fault (core dumped)
```
That's not so good.. It mostly means that there's some error in your memory management.. I have segmentation faults very rarely and if they occur the only thing that solves them here is a reboot.. Already tried that?

---

### Post by amanita on 2006-11-12
I rebooted comp and again got the same 

[HTML](synaptic:5569): Gtk-CRITICAL **: gtk_tree_model_get_iter: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(synaptic:5569): Gtk-CRITICAL **: gtk_tree_model_get: assertion `GTK_IS_TREE_MODEL (tree_model)' failed
Segmentation fault (core dumped)[/HTML]

I am lost :(

---

### Post by puppy on 2006-11-13
There are other threads on this - I'm running Edgy and it appears that "lock version" is *broken*. I'm surprised that more people aren't having difficulties - I have to lock a version of amarok because the one from the repositories lacks support I need. I'm basically having to ignore the "updates available" icon for the moment because I can't "lock" it - as you've experienced, Synaptic just closes and doesn't lock the version... :rolleyes:

---

### Post by amanita on 2006-11-27
I am wondering if anyone has found fix on that. I am not keen on reinstalling Synaptic, just because cannot lock version of the package :(

---

