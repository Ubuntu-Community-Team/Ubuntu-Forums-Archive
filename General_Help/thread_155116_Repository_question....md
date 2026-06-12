---
title: "Repository question..."
date: 2006-04-04
forum: General Help
---

### Post by MJSOnline on 2006-04-04
Hi all...  If I download source files of packages not listed in the repository to a folder on my hard drive can I put the folder address, e.g. /media/SD/Packages, into my sources list and let Ubuntu read the packages to install?  How do I do this?  Thanks. Matthew

---

### Post by carlosqueso on 2006-04-04
I may not understand.....If you are going to install from source code....then no, you need to compile and install them. Let me know if you need directions for this, cause I can't be bothered to type them out if it's not what you want. If they are .deb packages, you need to install them with dpkg and apt can manage them from there.  If it's something else, please explain a bit more clearly and someone should be able to help.

---

### Post by MJSOnline on 2006-04-04
[QUOTE=carlosqueso]I may not understand.....If you are going to install from source code....then no, you need to compile and install them. Let me know if you need directions for this, cause I can't be bothered to type them out if it's not what you want. If they are .deb packages, you need to install them with dpkg and apt can manage them from there.  If it's something else, please explain a bit more clearly and someone should be able to help.[/QUOTE]

Ok.   I want to install things like xdvdshrink and other packages that are not in the repository.

What packages or source applications do I need to download and how do I put them in my sources list so that Synaptic Package Manager can see them. I can then select them and let Synaptic Package Manager install / configure them...

So I have a folder called Packages and one called sources.  Both have for example xdvdshrink in them.  One a deb and one a source file.

I then want to put the folder address into my sources list so, /media/SD/Packages - and - /media/SD/Sources.

Does that make sense? M

---

### Post by MJSOnline on 2006-04-04
Anyone got any ideas? M

---

### Post by carlosqueso on 2006-04-04
I don't think what you want to do is possible.  If you install the debs with ```
sudo dpkg -i <deb file>
``` they will properly install and synaptic/apt will be able to see them.  If you need to install from the source, you should install checkinstall from the repos, and then use ```
./configure
make
checkinstall
``` to install the source.  It will create a .deb and install it, so synaptic/apt will be able to see it.  You can then remove the package with apt, and a newer ubuntu version should be able to overwrite it if the version is done properly.  Hope this is the information you are looking for.

---

### Post by MJSOnline on 2006-04-10
[QUOTE=carlosqueso]I don't think what you want to do is possible.  If you install the debs with ```
sudo dpkg -i <deb file>
``` they will properly install and synaptic/apt will be able to see them.  If you need to install from the source, you should install checkinstall from the repos, and then use ```
./configure
make
checkinstall
``` to install the source.  It will create a .deb and install it, so synaptic/apt will be able to see it.  You can then remove the package with apt, and a newer ubuntu version should be able to overwrite it if the version is done properly.  Hope this is the information you are looking for.[/QUOTE]

This thata the case that ubuntu only looks for deb files then why is the default sources list have src, sources, in it? How does Ubuntu install them on its own? M

---

### Post by Ramses de Norre on 2006-04-10
From the apt-get man pages:
> _source_ 
source causes apt-get to fetch source packages. APT will examine
              the  available packages to decide which source package to fetch.
              It will then find and download into the  current  directory  the
              newest available version of that source package. Source packages
              are tracked separately from binary  packages  via  deb-src  type
              lines  in the sources.list(5) file. This probably will mean that
              you will not get the same source as the  package  you  have  in&#8208;
              stalled  or  as  you  could install. If the --compile options is
              specified then the package will be compiled to a binary .deb us&#8208;
              ing  dpkg-buildpackage, if --download-only is specified then the
              source package will not be unpacked.

              A specific source version can be  retrieved  by  postfixing  the
              source  name with an equals and then the version to fetch, simi&#8208;
              lar to the mechanism used for the package  files.  This  enables
              exact matching of the source package name and version, implicit&#8208;
              ly enabling the APT::Get::Only-Source option.

              Note that source packages are not tracked like binary  packages,
              they  exist  only  in  the  current directory and are similar to
              downloading source tar balls.


---

### Post by MJSOnline on 2006-04-10
[QUOTE=Ramses de Norre]From the apt-get man pages:[/QUOTE] So I can  create a folder called sources o my hard drive and get my sources list to point to it?  Do I need any other file within the folder apart from the tar files? An index file, what sort? M

---

### Post by MJSOnline on 2006-04-10
Anyone got the answer? Thanks. M

---

### Post by jbennett on 2006-04-10
I don't think that you can just make up a folder and add it to your sources.list. As far as I know, you can only add the actual repositories to that file.
 
To install a .deb file do what carlos said and use dpkg... if you have a source file then you need to install checkinstall and then do ./configure... etc.

---

### Post by az on 2006-04-10
[QUOTE=MJSOnline]So I can  create a folder called sources o my hard drive and get my sources list to point to it?  Do I need any other file within the folder apart from the tar files? An index file, what sort? M[/QUOTE]

No.

A debian or Ubuntu developer work on packages at the source code level.  They upload their packages to the server in source form.  They actually have to package it before they upload it.  The source must conform to a set of packaging standards as well must the binary packages that the autobuilders make out of the source packages that the devs upload.

Any source you get directly from the applications' home page (upstream) is just a tarball.  To turn that tarball into a deb package that apt can use, you have to do some work.  A lot of work.  Deb packaging can be very complicated, which is why it works so well - there is a high stadard to maintain.

Basically, the tarball is unpacked, you create a debian directory with a rules makefile in it.  You write a control file to determine what packages the source will make, what dependencies they will all have.  You write pre-install, post-install, pre-remove and post remove scripts. You make sure the licencing is properly provided.  You make sure it conforms to all the other rules, too.  Then you make a .dsc file and rename to tarball to .orig.tar.gz and make a .diff file of all your chages.  Those three files are the things you need to build a deb package from source.

Just use checkinstall to build a rudementary package on your own system.  If it refuses to install, it's because you have other software on your system that conflicts with it.

Also, use k9copy instead of xdvdshrink.

---

### Post by MJSOnline on 2006-04-10
Ah..  Not that simple then...  Ok thanks for the info  I will try K9..  Thanks again. M

---

