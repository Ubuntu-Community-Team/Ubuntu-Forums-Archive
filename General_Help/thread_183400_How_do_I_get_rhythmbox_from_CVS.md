---
title: "How do I get rhythmbox from CVS?"
date: 2006-05-27
forum: General Help
---

### Post by idn on 2006-05-27
Hi

I want to try and install rhythmbox from cvs but I am not sure which command I use to download the source from the server. I know how to compile stuff once its downloaded, I have done this with svn before, but I have never used cvs. The location of the code is here

[http://cvs.gnome.org/viewcvs/rhythmbox/](http://cvs.gnome.org/viewcvs/rhythmbox/)

Thanks!

---

### Post by hw-tph on 2006-05-28
First set the CVSROOT environment variable to the Gnome CVS server:```
export CVSROOT=":pserver:anonymous@anoncvs.gnome.org:/cvs/gnome"
```
...and then login:```
cvs login
```Just hit enter for the password. Finally, checkout the module you want:```
cvs -z3 checkout rhythmbox
```

You can update the sources later by cd'ing to the rhythmbox directory and type **cvs up**.

Håkan

---

### Post by tkjacobsen on 2006-05-28
One of the developers have build an unofficial repo with a newer version of rhythmbox and gaim 2.

deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

it is version 0.9.4.1

---

### Post by Gustav on 2006-05-28
Or you can go to this site for .debs: [http://mighmos.org/packages.php](http://mighmos.org/packages.php)

---

### Post by SlugO on 2006-06-14
Anyone managed to build Rhythmbox CVS with the album art patch from [here]("http://bugzilla.gnome.org/show_bug.cgi?id=307848")? It's described on the developer's blog [here]("http://doctau.blogspot.com/2006/03/python-hacking-and-art-display.html").

I tried it but I haven't really built anything from CVS before or applied patches to them so I only got a Rhythmbox which didn't have working options and plugins windows...

---

### Post by doclivingston on 2006-06-16
If you're building from CVS you don't need to apply the patch, it (well, a better version) is already in CVS. All you should need to do is build current cvs with Python plugins enabled. Or just wait a day or so until 0.9.5 comes out.

---

