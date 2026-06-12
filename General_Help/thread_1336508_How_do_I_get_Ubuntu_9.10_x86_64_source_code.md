---
title: "How do I get Ubuntu 9.10 x86_64 source code?"
date: 2009-11-24
forum: General Help
---

### Post by wkulecz on 2009-11-24
Title says it all. How do I get Ubuntu 9.10 x86_64 source code?

I can't get synaptic to show me any source code packages.

I need the gstreamer sources used to build the packages distributed with 9.10 x86_64.

--wally.

---

### Post by Slim Odds on 2009-11-24
System->Administration->Software Sources

Check "Source Code"

---

### Post by wkulecz on 2009-11-25
> **Slim Odds said:**
> System->Administration->Software Sources

Check "Source Code"

Check box doesn't stick :(
It changes color but never displays as checked.

--wally.

---

### Post by pbr on 2009-12-14
I encountered the same thing today on an unbuntu 9.10 netbook remix install - trying to select "source code" in the "software sources" app doesn't show a checkmark; it changes the background color from white to brown but doesn't show a checkmark.

This is a crucial prerequisite for such important steps as this one: [http://blog.technicallyworks.com/2009/10/getting-hp-mini-1000-wireless-to-work.html](http://blog.technicallyworks.com/2009/10/getting-hp-mini-1000-wireless-to-work.html)

I have a co-worker who's new to Linux trying to get it to work on the HP mini 1000; this is the only true hurdle we've encountered.

Any pointers to how to get past this would be greatly appreciated.
-pbr

---

### Post by plucky on 2009-12-15
> Any pointers to how to get past this would be greatly appreciated.
-pbr 

I had to select "Main Server" and then it would allow me to tick the box to download the sources.

Good Luck

---

### Post by pbr on 2009-12-15
THANK YOU - that did the trick.  Plucky, you rock! 
My co-worker is a happy camper.

:D :D :D -pbr

---

### Post by wkulecz on 2009-12-31
Main server is really slow for me compared to some of the alternatives, but I switched to main server, did reload, but still no source packages are displayed in Synaptic :(

What is the trick?

---

### Post by jocko on 2009-12-31
The source packages will not be visible in synaptic. To get the source for a specific package (works for all packages in the standard repos, and probably most or all ppa repos):
```
apt-get source [COLOR=Blue]packagename[/COLOR]
```Note that you should run this within your home directory (or a subfolder in it) and you should NOT use sudo.

---

### Post by wkulecz on 2010-01-06
> apt-get source packagename

This does not work:

apt-get source gstreamer
either with or without sudo.  I've tried most of the package names that I seen in synaptic when I search for gstreamer.

Without being able to browse in synaptic how do I figure out the source package names?

apt-get source blender seems to work (I don't need it but it was a package name I was pretty sure of) so either gstreamer sources for 9.10 are not available or the package names are something I don't know.  This at least verifies I've got the repos right.

This created a blender source tree and let two *.gz and a *.dsc file in my home directory.  

Now what is the apt-get way to uninstall the sources?

--wally.

---

### Post by jocko on 2010-01-07
> **wkulecz said:**
> This does not work:

apt-get source gstreamer
either with or without sudo.  I've tried most of the package names that I seen in synaptic when I search for gstreamer.

Without being able to browse in synaptic how do I figure out the source package names?

apt-get source blender seems to work (I don't need it but it was a package name I was pretty sure of) so either gstreamer sources for 9.10 are not available or the package names are something I don't know.  This at least verifies I've got the repos right.

This created a blender source tree and let two *.gz and a *.dsc file in my home directory.  

Now what is the apt-get way to uninstall the sources?

--wally.
To find the name of the source package for a specific package, you could use apt-cache:
```
apt-cache search gstreamer -n
```will list the names and short descriptions of all packages with "gstreamer" in their name.
To get specific information about a particular package:
```
apt-cache showsrc libgstreamer0.10-0
```will show some information about the source package used to build the package "libgstreamer0.10-0":
```
jocko@jocko-desktop:~$ apt-cache showsrc libgstreamer0.10-0
[COLOR=Blue]Package: gstreamer0.10[/COLOR]
[COLOR=Blue]Binary: libgstreamer0.10-0, libgstreamer0.10-0-dbg, libgstreamer0.10-dev, gstreamer0.10-doc, gstreamer0.10-tools, gstreamer-tools[/COLOR]
Version: 0.10.25-2
Priority: optional
Section: libs
Maintainer: Maintainers of GStreamer packages <pkg-gstreamer-maintainers@lists.alioth.debian.org>
Build-Depends: debhelper (>= 5), cdbs (>= 0.4.20), gnome-pkg-tools (>= 0.7), autotools-dev, libxml2-dev (>= 2.6.0), zlib1g-dev (>= 1:1.1.4), libglib2.0-dev (>= 2.16), libgmp3-dev, libgsl0-dev, pkg-config (>= 0.11.0), bison (>= 1.875), flex (>= 2.5.34), dpkg-dev (>= 1.14.13), lsb-release, perl-doc, libgirepository1.0-dev (>= 0.6.3), gobject-introspection (>= 0.6.3), gobject-introspection-glib-2.0 (>= 0.6.3), gobject-introspection-freedesktop (>= 0.6.3)
Build-Depends-Indep: python (>= 2.2), gtk-doc-tools (>= 0.7), jade (>= 1.2.1), transfig (>= 3.2.3.c), docbook-utils (>= 0.6.9), docbook-xml, docbook-xsl, xsltproc (>= 1.0.21), ghostscript, xmlto, netpbm, libxml2-doc, libglib2.0-doc
Architecture: any
Standards-Version: 3.8.3
Format: 1.0
Directory: pool/main/g/gstreamer0.10
Files:
 ed5799dcd33bbb5154318f93d4194162 2092 gstreamer0.10_0.10.25-2.dsc
 3b0af3cc6899f04e3a0bad341095b79c 3980234 gstreamer0.10_0.10.25.orig.tar.gz
 5210acea5ec7f9badd567811bab5e455 40139 gstreamer0.10_0.10.25-2.diff.gz
Uploaders: David I. Lehn <dlehn@debian.org>,           Loic Minier <lool@dooz.org>,           Sebastien Bacher <seb128@debian.org>,           Sebastian Dröge <slomo@debian.org>,           Sjoerd Simons <sjoerd@debian.org>
Homepage: http://gstreamer.freedesktop.org
Checksums-Sha1: 
 b430931608b4c4c05d3ac0e1e4d1e9413aa1ed6f 3980234 gstreamer0.10_0.10.25.orig.tar.gz
 e73652f3f731bc66d0d3ba45b511bb716bdeacf5 40139 gstreamer0.10_0.10.25-2.diff.gz
Checksums-Sha256: 
 324546550a193d9eaebcb0779a545644b98144f735f57edf4fdfb2f1b6dfe393 3980234 gstreamer0.10_0.10.25.orig.tar.gz
 389d8d801b06f3fb8e02d478718ad63630ff160006146cde502d231f6f1079c4 40139 gstreamer0.10_0.10.25-2.diff.gz
```The "Package" line gives you the name of the source package, and the "Binary" line gives you the names of the packages that is built from that source. In this case the name of the source package is "gstreamer0.10", so:
```
apt-get source gstreamer0.10
```will give you the source.

And to "uninstall" sources: Just delete the files. "apt-get source" does not install anything in your system, it just downloads the source and unpacks it.

---

### Post by PGScooter on 2010-01-07
the thing with the checkbox not being checked sounds like a bug to me. Is it? If so, please post a bug report. Even if its not supposed to be checked, it sounds like a warning or something should pop up, no?

---

### Post by wkulecz on 2010-01-07
> And to "uninstall" sources: Just delete the files. "apt-get source" does not install anything in your system, it just downloads the source and unpacks it.

Thanks, that was my guess but I wanted to know for sure before I started deleting things -- my 9.10 test system is on a fairly small drive.


> the thing with the checkbox not being checked sounds like a bug to me. Is it? If so, please post a bug report. I suspect not all the mirrors want to carry the source packages.  I think the not checkmarking is trying to tell me the mirror doesn't carry it, albeit not very clearly.


> 
apt-cache search gstreamer -n
apt-cache showsrc libgstreamer0.10-0


Thanks a ton.  I don't do this often enough to be an apt-get expert and definitely prefer package selection with a graphical tool like symantic.

I'll add these to my cache of useful commands like apt-get update; apt-get upgrade for when the update manager screws up and tells me there are updates but won't download them.

apt-get source gstreamer0.10 seems to be working, I'd tried apt-get source gstreamer and apt-get source gstreamer-0.10 :(

--wally.

---

