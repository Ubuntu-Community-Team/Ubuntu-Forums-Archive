---
title: "administrative applications wont start"
date: 2006-06-14
forum: General Help
---

### Post by hoehaver on 2006-06-14
first of all i can start an adminastrative application i first noticed this...well just now it says i have one new update so i clicked it and it tryed to start but wouldnt so then i went to system>adm.> synamatic package whatever and it didnt work there and when i typed sudo apt-get update in a termanal it says ,john@:~$ sudo apt-get update
sudo: unable to lookup  via gethostbyname()
does anyone know what my problem is could it have anything to do with glib i installed the newest one so i could install gaim v v but i cant uninstall the old one bc alot of programs are using it so now i have two glibs installed?? can some one help

---

### Post by hoehaver on 2006-06-14
not can start but cant

---

### Post by bruce89 on 2006-06-14
I think it's the glib issue, unfortuneatly, you can't downgrade it if you can't work sudo AFAIK.

---

### Post by hoehaver on 2006-06-14
no it doesnt work, do you know of any other way to fix this problem beside reinstalling ubuntu. bc i really really dont want to do that

---

### Post by hoehaver on 2006-06-14
when i installed, or tryed to install gaim vv it said this 
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.11.0, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
how can i do this??bc if i can then i believe this will fix my problem

---

### Post by bruce89 on 2006-06-14
Again, in order to change any files outside your home directory, you have to use sudo.  It looks like you are stuck with a reinstall.

---

