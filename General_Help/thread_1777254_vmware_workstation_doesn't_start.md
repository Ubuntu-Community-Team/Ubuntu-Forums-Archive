---
title: "vmware workstation doesn't start"
date: 2011-06-07
forum: General Help
---

### Post by nixIT on 2011-06-07
Hello all,

installed VMWare workstation by following the steps on [this page]("http://geekyprojects.com/ubuntu/how-to-install-vmware-7-on-ubuntu-11-04/").  Everything seemed to install ok, I have a VMWare Workstation and VMWare Player link in my System menu, but when I click them nothing launches.

I even rebooted to see if that would help, nada.

any ideas how I can launch VMWare Workstation?  Need to set up a couple Windows clients.

--nixIT

---

### Post by Toz on 2011-06-07
Open a terminal window, type in the following command and then try again.```
sudo apt-get install libgtkmm-2.4-1c2a
```

---

### Post by nixIT on 2011-06-07
> **Toz said:**
> Open a terminal window, type in the following command and then try again.```
sudo apt-get install libgtkmm-2.4-1c2a
```

@Toz,

That fixed it.  Can you explain what that does and why it works?

--nixIT

---

### Post by Toz on 2011-06-07
As I understand it, vmware tries to do its own GTK rendering, but the default ubuntu install doesn't include the library that it needs to accomplish this. If you had run vmware from the command line prior to the fix, you would have seen alot of messages about GTK version being too old.

From: ```
apt-cache show libgtkmm-2.4-1c2a
```> Description: C++ wrappers for GTK+ (shared libraries)
 Gtkmm is a C++ interface for the popular GUI library GTK+, API version 2.4.
 Gtkmm provides a convenient interface for C++ programmers to create
 graphical user interfaces with GTK+'s flexible OO framework. Highlights
 include type safe callbacks, widgets extensible using inheritance and
 over 180 classes that can be freely combined to quickly create complex
 user interfaces.


If you don't mind, can you flag this thread as solved from the Thread Tools link above so that others may benefit from the fix? Thanks.

---

### Post by nixIT on 2011-06-07
Thank you for the explanation.

---

