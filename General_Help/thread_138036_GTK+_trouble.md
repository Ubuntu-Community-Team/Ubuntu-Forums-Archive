---
title: "GTK+ trouble"
date: 2006-03-01
forum: General Help
---

### Post by Bisschop on 2006-03-01
I'm pretty new to linux and ubuntu but I decided to give it a try
But now I downloaded ethereal and unpacked it and run ./configure
but at the end it says:

checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for pkg-config... (cached) /usr/local/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: GLib2 distribution not found.

If i try to run the "make" file it gives an error that the make file doesn't exist

when installing ubuntu I chose the default installation and when I go to synaptic and do a search on GTK all the packages that show up are installed, and the same for glib.
I also installed nmap, that did install but I can't use the GUI.

I hope that somebody can tell me what's wrong.

---

### Post by dcstar on 2006-03-01
[QUOTE=Bisschop]I'm pretty new to linux and ubuntu but I decided to give it a try
But now I downloaded ethereal and unpacked it and run ./configure
but at the end it says:
.......[/QUOTE]
What is wrong with just installing the package available from the repositories instead of stuffing around with compiling?

---

### Post by Zalbor on 2006-03-01
Did you try to download it from the repositories, instead of source?
I don't know what the problem is from source, but it could be that ubuntu uses "specialised" versions of GTK etc, so the configure script can't recognize them. But the repository one should work!

---

### Post by psychicdragon on 2006-03-01
You need the dev packages to build it.

**sudo apt-get install libgtk2.0-dev libglib2.0-dev** and it should build ok.

That said, ethereal is in the repositories.

---

### Post by Bisschop on 2006-03-01
Like I sayd I'm pretty new to linux and ubuntu and I don't know where the repositories are and how to use them.
I did do a serach for ethereal in saynaptic packetmanager but no results showed up and I also tried "sudo apt-get install ethereal" and it gave me an error to 
so can tell somebody me how to install ethereal?

and I also tried "sudo apt-get install libgtk2.0-dev libglib2.0-dev" but it gave me an error than.

And thanks for the fast replies

---

### Post by jeremiebergeron on 2006-03-01
First off, you probably need to add the universe repositories to apt-get. There's numerous sites out there that mention how to do this. You probably want to add the multiverse repositories as well so that you can find most software packages.

Also, concerning building packages from source. By default, ubuntu doesn't include and development packages so you can't build from source. However you can install them but I really haven't ever had to (pretty much everything can be found in universe and multiverse).

Hope that helps!

---

### Post by Bisschop on 2006-03-02
Oke thanks, it works fine now

---

