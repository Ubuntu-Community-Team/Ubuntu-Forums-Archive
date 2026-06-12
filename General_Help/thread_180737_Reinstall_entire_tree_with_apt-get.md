---
title: "Reinstall entire tree with apt-get?"
date: 2006-05-22
forum: General Help
---

### Post by mattlach on 2006-05-22
Hi..

I recently had some partition failure problems and it caused some important files to be deleted.

I can still run apt-get though.

Is there a way to tell apt get to reinstall everything thats recorded in the installed tree with all dependancies?

I was experimenting with apt-get install --reinstall, but I can only figure out how to install one package at a time.

Is there a way to tell it to reinstall every single installed package?

Thanks,
Matt

---

### Post by olsonar on 2006-05-22
if you have a GUI and can use Synaptic, just use it, goto the 'status' section, click 'installed' click on a package, Ctrl + A to select all, right-click, reinstall, apply.

---

### Post by mattlach on 2006-05-23
Unfortunately synaptic is one of the corrupted apps, so I am trying to do it from the console.

I reinstalled synaptic alone from the console, but it still wont start, so I am assuming that one of its dependancies is corrupt.

So there is no command line switch to reinstall all?

Where is the list of installed packages recorded?   Maybe I can read that and just add them all to a long apt-get command line?

Thanks,
Matt

---

### Post by olsonar on 2006-05-23
you can find a list of synaptic's dependencies here: [http://packages.ubuntu.com/dapper/admin/synaptic](http://packages.ubuntu.com/dapper/admin/synaptic)

try reinstalling them as well.

---

