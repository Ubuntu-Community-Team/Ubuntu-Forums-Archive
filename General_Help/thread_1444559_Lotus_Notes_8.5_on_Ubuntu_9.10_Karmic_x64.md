---
title: "Lotus Notes 8.5 on Ubuntu 9.10 Karmic x64"
date: 2010-04-01
forum: General Help
---

### Post by ABitTooSpicy on 2010-04-01
Hi Everyone,

Hope you don't mind helping out a newbie... so I am trying to get Notes to run on Ubuntu 9.10 karmic x64 and haven't had any luck.

I started off by following the steps from the following location
[http://www-10.lotus.com/ldd/nd85forum.nsf/0/69b50f2db7bb7b0b85257659005ab79e?OpenDocument](http://www-10.lotus.com/ldd/nd85forum.nsf/0/69b50f2db7bb7b0b85257659005ab79e?OpenDocument)
This didn't work and I had the symptoms listed below.  

I then looked at the following guide and did all the steps that were not on the above link:
[http://metkhoo.blogspot.com/2010/03/notes-851-on-ubuntu-910-karmic-x64.html](http://metkhoo.blogspot.com/2010/03/notes-851-on-ubuntu-910-karmic-x64.html)
However I still had the same issue.

So the symptoms:
1) I don't see notes in the apps->office menu, but I am able to start it via:
cd /opt/ibm/lotus/notes/framework
../notes
2) I get the login window and am able to go through the setup (pointing to the notes id file, and my domino server etc). However at the end of it all, no GUI is displayed. Even though lnotes shows up in the running processes.
3) In the terminal window I get the following error:

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(:6077): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(:6077): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(:6077): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(:6077): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(:6077): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(:6077): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(:6077): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(:6077): Gdk-CRITICAL **: gdk_x11_atom_to_xatom_for_display: assertion `atom != GDK_NONE' failed
04/01/2010 11:17:22.30 AM [06077:00002--207587472] DeskClientOpenInt> Calling CreateProgramRCP pszRCPCmdLine[/authenticate ] bDeskProvisioningRestart [0]
04/01/2010 11:17:22.30 AM [06077:00002--207587472] DeskClientOpenInt> Executed CreateProgramRCP

Let me know what you think. Your help is greatly appreciated!

---

### Post by ABitTooSpicy on 2010-04-01
Giving it a bump in case anybody in the evening crowd has some suggestions...  :-D

---

### Post by ABitTooSpicy on 2010-04-04
Just thought I should post this.  I never really figured out what I did wrong the first time but I now have everything working.  

I reinstalled Ubuntu 9.10 Karmic 64 bit and then before applying any fixes or updates I followed this guides every single step:

[http://metkhoo.blogspot.com/2010/03/notes-851-on-ubuntu-910-karmic-x64.html](http://metkhoo.blogspot.com/2010/03/notes-851-on-ubuntu-910-karmic-x64.html)

I now have Lotus Notes working perfectly!

---

