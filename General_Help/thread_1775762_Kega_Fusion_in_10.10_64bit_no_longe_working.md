---
title: "Kega Fusion in 10.10 64bit no longe working"
date: 2011-06-05
forum: General Help
---

### Post by jamesensor on 2011-06-05
Hi all, I'm used to come here looking for help reading posts and not bother posting repeated questions, however this time I'm clueless. I'm running ubuntu 10.10 and I used to play sega genesis games in kega fusion emulator downloaded from [http://www.eidolons-inn.net/tiki-index.php?page=Kega](http://www.eidolons-inn.net/tiki-index.php?page=Kega)

Problem is that now I can't run it. Perhaps because of the updates. It used to work in the past (with maverick).

Here's the terminal feedback

(Fusion:3299): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(Fusion:3299): Gtk-WARNING **: Loading IM context type 'ibus' failed
Segmentation fault

It's the only emu I know to work on ubuntu 10.10 64bit :( 
My kernel is 2.6.35-28 with gnome 2.32.0

Hope someone can help. Thanks

EDIT:

After reading some stuff about forcing i386 architecture on 64bit, I tried to install Gens GS on my system with


/Downloads$ sudo dpkg --force-architecture -i Gens_2.16.7_i386.deb 

Results: Installed and worked perfectly. Hope it helps someone with the same issues. Regards

---

