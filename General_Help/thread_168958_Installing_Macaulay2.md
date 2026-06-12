---
title: "Installing Macaulay2"
date: 2006-05-01
forum: General Help
---

### Post by -Phi- on 2006-05-01
I am trying to install Macaulay 2 on Ubuntu 5.10 and have had little success.

My first attempt was to run alien on the [Macaulay2 rpm version]("http://download.fedora.redhat.com/pub/fedora/linux/extras/3/i386/") and install from the resulting .deb. But when I tried to run Macaulay2, it could not find the correct libraries (ie. the Fedora Core versions of the libraries I assume), though libgdbm3 package is installed.
> /usr/lib/Macaulay2-0.9.2/libexec/Macaulay2: error while loading shared libraries: libgdbm.so.2: cannot open shared object file: No such file or directory

My next attempt was to install from [the sourceforge version]("http://sourceforge.net/project/showfiles.php?group_id=138417") instead, following the included install instructions (untar, make link in /usr/bin/). However, when I tried to run M2, it came up with the error "illegal instruction" and nothing more.

[Macaulay2 Homepage]("http://www.math.uiuc.edu/Macaulay2/")

Any suggestions?

- Phi

---

### Post by -Phi- on 2006-05-02
Solved :D

Future reference for anyone else that tries this:

~ Use alien on Macaulay2-0.9.2-14.i386.rpm version ([available here]("http://download.fedora.redhat.com/pub/fedora/linux/extras/3/i386/")).
~ Install the .deb file. 
~ Make a symbolic link in /usr/lib/ called libgdbm.so.2 to libgdbm.so.3.0.0 (this solves the error I was getting).
~ Run using the command M2.

I'm sketchy as to whether the link step is a good idea or not. It seems a bit bandaid and I suspect there is a better way to do it.

I could not get the 9.8 version of Macaulay2 to work in the same way. I suspect it needs a newer version of a library that I don't have in breezy.

- Phi

---

### Post by glennric on 2006-07-27
I installed the Macaulay2-0.9.2-i686-Linux-2.4.20.tar.gz version by untarring into /usr/local/ and making a link from /usr/local/Macaulay2 to /usr/local/Macaulay2-0.9.2 and a link from /usr/bin/M2 to /usr/local/Macaulay2/bin/M2.  I didn't have the problem you had with libgdbm3 that you had.  Perhaps this is because I am running Ubuntu 6.04.

I have also had no success with the Macaulay2-0.9.8 version.  I get the illegal instruction too.  Have you had any luck with this?

---

### Post by -Phi- on 2006-07-27
Macaulay2 0.9.2 hasn't given me any troubles (though running it through TeXmacs has given some formatting issues) so I never went back to try 0.9.8. I'm just glad it works.

Glad that the library issue can be solved by a less bandaidish solution :) Maybe someday Macaulay2 will make it into the repositories.

- Phi

---

### Post by glennric on 2006-07-28
I always try to get the newest version of Macaulay2 whenever possible.  I always hope that they will include improved groebner basis algorithms and bug fixes that will allow me to compute more complex examples for my research.  I will probably eventually find a way to install the new version.  If I have to compile it myself I will.

---

### Post by -Phi- on 2006-08-02
Thought you'd want to know that there's a new version of Macaulay2 and it works fine for me. You can download 0.9.20 (different from 0.9.2) here: [http://www.math.uiuc.edu/Macaulay2/Downloads/Test-Versions/](http://www.math.uiuc.edu/Macaulay2/Downloads/Test-Versions/)

I had to make some links similar to the ones you listed to get rid of errors.

A big improvement is that it handles displaying long equations better. Instead of wrapping the exponents separate from the variables it wraps them legibly. It's also got extensive documentation (whee!).

Unfortunately TeXmacs can't deal with the new version, but following the instructions in the INSTALL file wrote a .emacs file. It runs just fine in emacs.

For some reason M2 wouldn't run on my supervisor's Mandriva machine. It didn't spit errors or anything, just sat there.

Good Luck!

- Phi

---

### Post by glennric on 2006-08-02
Yeah, I saw that one, but haven't gotten around to trying it out yet.  Thanks for the heads up.

---

### Post by glennric on 2006-11-03
Macaulay 2 is now available as a deb on the Macaulay 2 website in the test versions.  It seems to work fine.

Edit:  Watch out when you run setup() from M2.  This will add the appropriate things to .emacs and .bashrc; however, the MANPATH it creates will override the default man paths.  You won't be able to read any other man pages.  I had to comment out the MANPATH stuff in the .bashrc file.

---

