---
title: "libgdk-1.2.so.0 and gsview"
date: 2012-05-05
forum: General Help
---

### Post by Flos Headford on 2012-05-05
I am running Ubuntu 10.04 LTS. I am trying to get gsview working. I followed the instructions on the GSview website, but get no response when trying to start gsview using the GUI. When, in a terminal, I navigate to the appropriate directory and try to start gsview, I get the following:

/usr/local/bin$ gsview
gsview: error while loading shared libraries: libgdk-1.2.so.0: cannot open shared object file: No such file or directory

I cannot find this file on my system. I presume it is supposed to be a link, but I don't know where it ought to reside, or what it should point to.

I have already used Synaptic to install everything that starts libgdk.

I would be grateful for any info so that I can fix this.
Phil

---

### Post by Flos Headford on 2012-05-31
I have managed to fix this.

Even the latest gsview apparently uses the 1.2 version of GTK and GDK, which have been removed from Ubuntu's repositories. GTK and GDK are currently version 2.0.
I located the .debs for the 1.2 versions and installed them.
I also needed to create  a link named libgs.so which pointed to the main GTK library.

Flos

---

